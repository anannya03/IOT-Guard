<script>
import { Line, mixins } from "vue-chartjs";
import axios from "axios";

export default {
  extends: Line,
  mixins: [mixins.reactiveData],
  data() {
    return {
      chartData: "",
      // set chart options
      options: {
        scales: {
          yAxes: [
            {
              ticks: {
                beginAtZero: true,
                fontSize: 12,
                fontColor: "#494949",
                fontFamily: "Montserrat Alternates",
              },
              gridLines: {
                display: true,
              },
            },
          ],
          xAxes: [
            {
              ticks: {
                beginAtZero: true,
                fontSize: 12,
                fontColor: "#494949",
                fontFamily: "Montserrat Alternates",
              },
              gridLines: {
                display: false,
              },
            },
          ],
        },
        legend: {
          display: true,
          labels: {
            fontSize: 12,
            fontColor: "#494949",
            fontFamily: "Montserrat Alternates",
          },
        },
        responsive: true,
        maintainAspectRatio: false,
      },
    };
  },
  mounted() {
    // render chart dynamically
    this.renderChart(this.chartData, this.options);
  },
  created() {
    axios
      .get(`https://fast-api-demo-api.herokuapp.com/values/`)
      .then((response) => {
        // JSON responses are automatically parsed.
        const responseData = response.data;
        console.log(responseData);
        // create the chart
        this.chartData = {
          labels: responseData.map((item) => item.facts),
          datasets: [
            // dataset 1
            {
              label: "MQ2 Values",
              borderColor: "#1A3850",
              borderWidth: 2,
              fill: false,
              lineTension: 0,
              backgroundColor: "#1A3850",
              data: responseData.map((item) => item.MQ2_value),
            },
            // dataset 2
            {
              label: "MQ7 Values",
              borderColor: "#9D2929",
              borderWidth: 2,
              fill: false,
              lineTension: 0,
              backgroundColor: "#9D2929",
              data: responseData.map((item) => item.MQ7_value),
            },
          ],
        };
      })
      .catch((e) => {
        this.errors.push(e);
      });
  },
};
</script>

<style scoped></style>

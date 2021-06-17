<script>
import { Line, mixins } from "vue-chartjs";
import axios from "axios";

export default {
  extends: Line,
  mixins: [mixins.reactiveData],
  methods: {
    makeRequest() {
      // make a GET request to get the last 15 values
      axios
        .get(`https://iaq-monitor-api.herokuapp.com/latestValues/`)
        .then((response) => {
          // JSON responses are automatically parsed.
          const responseData = response.data;
          console.log(responseData);
          // create the chart
          this.chartData = {
            labels: responseData.map(function(i) {
              return i.Date_Time.split(" ")[1];
            }),
            datasets: [
              // CO2 gas dataset
              {
                label: "CO2",
                borderColor: "#d8b384",
                borderWidth: 4,
                fill: false,
                lineTension: 0,
                backgroundColor: "#d8b384",
                data: responseData.map((item) => item.CO2),
              },
              // Toluene gas dataset
              {
                label: "Toluene",
                borderColor: "#f54748",
                borderWidth: 4,
                fill: false,
                lineTension: 0,
                backgroundColor: "#f54748",
                data: responseData.map((item) => item.Toluene),
              },
              // NH4 gas dataset
              {
                label: "NH4",
                borderColor: "#ff8474",
                borderWidth: 4,
                fill: false,
                lineTension: 0,
                backgroundColor: "#ff8474",
                data: responseData.map((item) => item.NH4),
              },
              // Acetone gas dataset
              {
                label: "Acetone",
                borderColor: "#8e9775",
                borderWidth: 4,
                fill: false,
                lineTension: 0,
                backgroundColor: "#8e9775",
                data: responseData.map((item) => item.Acetone),
              },
              // H2 gas dataset
              {
                label: "H2",
                borderWidth: 4,
                borderColor: "#cee5d0",
                fill: false,
                lineTension: 0,
                backgroundColor: "#cee5d0",
                data: responseData.map((item) => item.H2),
              },
              // LPG gas dataset
              {
                label: "LPG",
                borderWidth: 4,
                borderColor: "#325288",
                fill: false,
                lineTension: 0,
                backgroundColor: "#325288",
                data: responseData.map((item) => item.LPG),
              },
              // CH4 gas dataset
              {
                label: "CH4",
                borderWidth: 4,
                borderColor: "#4a503d",
                fill: false,
                lineTension: 0,
                backgroundColor: "#4a503d",
                data: responseData.map((item) => item.CH4),
              },
              // CO gas dataset
              {
                label: "CO",
                borderWidth: 4,
                borderColor: "#e28f83",
                fill: false,
                lineTension: 0,
                backgroundColor: "#e28f83",
                data: responseData.map((item) => item.CO),
              },
              // Alcohol gas dataset
              {
                label: "Alcohol",
                borderColor: "#907fa4",
                borderWidth: 4,
                fill: false,
                lineTension: 0,
                backgroundColor: "#907fa4",
                data: responseData.map((item) => item.Alcohol),
              },
            ],
          };
        })
        .catch((e) => {
          console.log(e);
        });
    },
  },
  data() {
    return {
      timer: null,
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
        animation: true,
      },
    };
  },
  mounted() {
    // render chart dynamically
    this.renderChart(this.chartData, this.options);
  },
  created() {
    this.timer = setInterval(() => {
      this.makeRequest();
    }, 11000);
  },
  beforeDestroy() {
    clearInterval(this.timer);
  },
};
</script>

<script>
import { Line, mixins } from 'vue-chartjs'
import axios from 'axios'

export default {
  extends: Line,
  mixins: [mixins.reactiveData],
  data() {
    return {
      chartData: '',
      // Axis Styling
      options: {
          scales: {
            yAxes: [{
              ticks: {
                beginAtZero: true
              },
              gridLines: {
                display: true
              }
            }],
            xAxes: [ {
              gridLines: {
                display: true
              }
            }]
          },
          legend: {
            display: true
          },
          responsive: true,
          maintainAspectRatio: false
        }
    }
  },
  mounted() {
    this.renderChart(this.chartData, this.options)
  },
  created() {
    axios.get(`https://fast-api-demo-api.herokuapp.com/values/`)
      .then(response => {
        // JSON responses are automatically parsed.
        const responseData = response.data
        console.log(responseData);
        // Creating the chart
        this.chartData = {
          labels: responseData.map(item => item.facts),
          datasets: [
            // Dataset 1
            {
            label: 'MQ2 Values',
            borderColor: '#1A3850',
            borderWidth: 2,
            fill:false,
            lineTension:0,
            backgroundColor: '#1A3850',
             data: responseData.map(item => item.MQ2_value)
            },
            // Dataset 2
            {
            label: 'MQ7 Values',
            borderColor: '#9D2929',
            borderWidth: 2,
            fill:false,
            lineTension:0,
            backgroundColor: '#9D2929',
            data: responseData.map(item => item.MQ7_value)
            }
          ]
        }
      })
      .catch(e => {
        this.errors.push(e)
      })
  }
}
</script>

<style scoped>
 canvas{
   padding-left: 150px;
   padding-right: 150px;
   margin-top: 50px;
 }
</style>
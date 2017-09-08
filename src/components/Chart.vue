<template>
  <div class="container">
    <div class="chart-title">Chart</div>
    <div class="chart">
      <canvas id="myChart" width="400" height="400"></canvas>
    </div>
  </div>
</template>

<script>
  import Chart from 'chart.js'

  export default {
    name: 'chart',
    data () {
      return {
      }
    },
    mounted () {
      this.initChart()
    },
    methods: {
      initChart () {
        let context = document.getElementById('myChart')
        let chart = new Chart(context, {
          type: 'bar',
          data: {
            labels: ['Red', 'Blue', 'Yellow', 'Green', 'Purple', 'Orange'],
            datasets: [{
              label: '# of Votes',
              data: [12, 19, 3, 5, 2, 3],
              backgroundColor: [
                'rgba(255, 99, 132, 0.2)',
                'rgba(54, 162, 235, 0.2)',
                'rgba(255, 206, 86, 0.2)',
                'rgba(75, 192, 192, 0.2)',
                'rgba(153, 102, 255, 0.2)',
                'rgba(255, 159, 64, 0.2)'
              ],
              borderColor: [
                'rgba(255,99,132,1)',
                'rgba(54, 162, 235, 1)',
                'rgba(255, 206, 86, 1)',
                'rgba(75, 192, 192, 1)',
                'rgba(153, 102, 255, 1)',
                'rgba(255, 159, 64, 1)'
              ],
              borderWidth: 1
            }]
          },
          options: {
            scales: {
              yAxes: [{
                ticks: {
                  beginAtZero: true
                }
              }]
            }
          }
        })
        console.log(chart)
      }
    }
  }
</script>

<style lang="stylus" scoped>
.container
  width 80vw
  height 80vh
  margin auto
  .chart-title
    font-size 25px
    text-align center
</style>

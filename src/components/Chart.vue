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
        measurements: [
          {
            date: '2014-08-30',
            size: '150', // in cm
            weight: '58' // in kg
          },
          {
            date: '2015-08-30',
            size: '154', // in cm
            weight: '65' // in kg
          },
          {
            date: '2016-08-30',
            size: '167', // in cm
            weight: '71' // in kg
          },
          {
            date: '2017-08-30',
            size: '173', // in cm
            weight: '80' // in kg
          }
        ],
        dates: [],
        sizes: [],
        weights: []
      }
    },
    mounted () {
      this.extractData(this.measurements)
      this.initChart()
    },
    methods: {
      extractData (data) {
        data.map((m) => {
          this.dates.push(m.date)
          this.sizes.push(m.size)
          this.weights.push(m.weight)
        })
      },
      initChart () {
        let context = document.getElementById('myChart')
        let chart = new Chart(context, {
          type: 'line',
          data: {
            labels: this.dates,
            datasets: [
              {
                label: 'Taille',
                data: this.sizes,
                borderColor: 'rgba(255, 159, 64, 1)',
                backgroundColor: 'rgba(255, 159, 64, 1)',
                fill: false,
                pointBackgroundColor: 'rgba(255, 159, 64, 1)',
                pointStyle: 'rect'
              },
              {
                label: 'Poids',
                data: this.weights,
                borderColor: 'rgba(153, 102, 255, 1)',
                backgroundColor: 'rgba(153, 102, 255, 1)',
                fill: false,
                pointBackgroundColor: 'rgba(153, 102, 255, 1)',
                pointStyle: 'rect'
              }
            ]
          }
        })
        chart.canvas.parentNode.style.height = '500px'
        chart.canvas.parentNode.style.width = '500px'
      }
    }
  }
</script>

<style lang="stylus" scoped>
.container
  display flex
  flex-direction column
  justify-content center
  max-width 80vw
  margin auto
  .chart-title
    font-size 25px
    text-align center
    margin-bottom 20px
  .chart
    margin auto
</style>

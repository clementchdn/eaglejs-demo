<template lang='pug'>
eg-transition(enter="lightSpeedIn" leave="fadeOut")
  .subslide
    .center(style="width:80%; height: 50%; margin-top: 2em")
      canvas(id='myChart')
</template>

<script>
import Chart from 'chart.js'
export default {
  props: {
    id: { default: () => Math.random().toString(36).substr(2, 10) },
    width: { default: 400 },
    height: { default: 400 },
    data: { default: () => ({}) },
    options: { default: () => ({}) },
    type: { default: 'bar' }
  },
  data: function () {
    return {
      myChart: null
    }
  },
  mounted: function () {
    var canvas = document.getElementById('myChart')
    var ctx = canvas.getContext('2d')
    // Reduce the animation steps for demo clarity.
    this.myChart = new Chart(ctx, {
      type: 'line',
      data: {
        labels: [3, 5, 10, 15, 20, 25, 50, 100, 200, 500],
        datasets: [{
          label: 'temps Gauss',
          data: [0, 0, 0, 0, 0, 0, 0.07810569, 0.29376864, 2.10183144, 32.31143546],
          borderWidth: 2,
          borderColor: 'blue',
          pointBackgroundColor: 'blue',
          pointBorderColor: 'black',
          fill: false,
          cubicInterpolationMode: 'monotone'
        },
        {
          label: 'temps Cholesky',
          data: [0.00000000e+00, 0.00000000e+00, 9.99689102e-04, 1.99437141e-03,
            1.27029419e-03, 0.00000000e+00, 3.29086781e-02, 1.21874332e-01, 8.13752651e-01, 1.25362077e+01],
          borderWidth: 2,
          borderColor: 'red',
          pointBackgroundColor: 'red',
          pointBorderColor: 'grey',
          fill: false,
          cubicInterpolationMode: 'monotone'
        }
        ]
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
  }
}
</script>

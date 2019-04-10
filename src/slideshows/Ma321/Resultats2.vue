<template lang='pug'>
eg-transition(enter="bounceInDown" leave="zoomOut")
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
        labels: [5, 10, 20, 50, 100],
        datasets: [{
          label: 'erreur Gauss',
          data: [1.36280344e1, 2.04125251e1, 5.72293854e2, 4.17479288e-15, 1.0310738e-15],
          borderWidth: 2,
          borderColor: 'blue',
          pointBackgroundColor: 'blue',
          pointBorderColor: 'black',
          fill: false,
          cubicInterpolationMode: 'monotone',
          lineTension: 0
        },
        {
          label: 'erreur Cholesky',
          data: [2.09784693e-12, 1.94209711e-15, 7.64644699e-15, 6.82345790e-13, 1.63807529e-13],
          borderWidth: 2,
          borderColor: 'red',
          pointBackgroundColor: 'red',
          pointBorderColor: 'grey',
          fill: false,
          cubicInterpolationMode: 'monotone',
          lineTension: 0
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

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
  methods: {
    readTextFile (file) {
    }
  },
  mounted: function () {
    this.readTextFile('./gauss-seidel_traite')
    var canvas = document.getElementById('myChart')
    var ctx = canvas.getContext('2d')
    // Reduce the animation steps for demo clarity.
    this.myChart = new Chart(ctx, {
      type: 'line',
      data: {
        labels: [3, 5, 10, 15, 20, 25, 50, 75, 100, 200, 500, 1000, 1001, 1010, 1050],
        datasets: [{
          label: 'temps Gauss',
          data: [0.00000000e+00, 0.00000000e+00, 0.00000000e+00, 0.00000000e+00,
            0.00000000e+00, 0.00000000e+00, 4.28886414e-02, 1.49932861e-01,
            2.86247730e-01, 2.07795119e+00, 3.32249317e+01, 2.65067729e+02,
            2.73051842e+02, 2.83206855e+02, 3.14005286e+02],
          borderWidth: 2,
          borderColor: 'blue',
          pointBackgroundColor: 'blue',
          pointBorderColor: 'black',
          fill: false,
          cubicInterpolationMode: 'monotone'
        },
        {
          label: 'temps Cholesky',
          data: [1.95623636e-01, 1.99961662e-03, 9.96589661e-04, 1.99437141e-03,
            5.70483208e-02, 0.00000000e+00, 3.12438011e-02, 6.24837875e-02,
            1.41240835e-01, 1.11279655e+00, 1.36044064e+01, 1.04207876e+02,
            1.02150656e+02, 1.06075644e+02, 1.16076639e+02],
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

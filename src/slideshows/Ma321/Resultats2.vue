<template lang='pug'>
eg-transition(enter="bounceInRight" leave="slideOutLeft")
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
      type: 'bar',
      title: {
        text: 'Erreurs pour des matrices de différentes tailles avec une précision de 1e-5'
      },
      data: {
        labels: ['5', '10', '25', '50', '100'],
        datasets: [{
          label: 'Gauss-Seidel',
          data: [2.107017308e-08, 1.788055175e-07, 1.0187008361193302e-06, 1.99519036867267e-06, 2.46262378175457e-06],
          backgroundColor: [
            'rgba(255, 206, 86, 0.2)',
            'rgba(255, 206, 86, 0.2)',
            'rgba(255, 206, 86, 0.2)',
            'rgba(255, 206, 86, 0.2)',
            'rgba(255, 206, 86, 0.2)'
          ],
          borderColor: [
            'rgba(255, 206, 86, 1)',
            'rgba(255, 206, 86, 1)',
            'rgba(255, 206, 86, 1)',
            'rgba(255, 206, 86, 1)',
            'rgba(255, 206, 86, 1)'
          ],
          borderWidth: 1
        }, {
          label: 'Jacobi',
          data: [1.4297224762000002e-07, 3.7032093300000005e-07, 1.18758685228507e-06, 2.09740262715863e-06, 8.152181431528799e-07],
          backgroundColor: [
            'rgba(255, 99, 132, 0.2)',
            'rgba(255, 99, 132, 0.2)',
            'rgba(255, 99, 132, 0.2)',
            'rgba(255, 99, 132, 0.2)',
            'rgba(255, 99, 132, 0.2)'
          ],
          borderColor: [
            'rgba(255, 99, 132, 1)',
            'rgba(255, 99, 132, 1)',
            'rgba(255, 99, 132, 1)',
            'rgba(255, 99, 132, 1)',
            'rgba(255, 99, 132, 1)'
          ],
          borderWidth: 1
        }, {
          label: 'SOR',
          data: [7.067551650000001e-06, 6.8045963099999996e-06, 6.476614218e-06, 6.798950429999999e-06, 7.130812200000001e-06],
          backgroundColor: [
            'rgba(54, 162, 235, 0.2)',
            'rgba(54, 162, 235, 0.2)',
            'rgba(54, 162, 235, 0.2)',
            'rgba(54, 162, 235, 0.2)',
            'rgba(54, 162, 235, 0.2)'
          ],
          borderColor: [
            'rgba(54, 162, 235, 1)',
            'rgba(54, 162, 235, 1)',
            'rgba(54, 162, 235, 1)',
            'rgba(54, 162, 235, 1)',
            'rgba(54, 162, 235, 1)'
          ],
          borderWidth: 1
        }]
      },
      options: {
        title: {
          display: true,
          text: 'Erreurs pour des matrices de tailles différentes pour chaque méthode avec une précision de 1e-5 ',
          fontsize: 12
        },
        scales: {
          yAxes: [{
            text: 'Temps de résolution en ms',
            display: true,
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

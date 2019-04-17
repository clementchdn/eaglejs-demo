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
    console.log(canvas)
    var ctx = canvas.getContext('2d')
    // Reduce the animation steps for demo clarity.
    this.myChart = new Chart(ctx, {
      type: 'bar',
      title: {
        text: 'Temps de résolution pour chaque méthode en fonction de la taille de la matrice A'
      },
      data: {
        labels: ['5', '10', '25', '50', '100', '250', '500', '1000'],
        datasets: [{
          label: 'Gauss-Seidel',
          data: [0.0281333, 0.05735561999999999, 0.26550237000000004, 0.9080718999999998, 7.66193567, 53.69801662, 369.5774218399999, 5623.299682940002],
          backgroundColor: [
            'rgba(255, 206, 86, 0.2)',
            'rgba(255, 206, 86, 0.2)',
            'rgba(255, 206, 86, 0.2)',
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
            'rgba(255, 206, 86, 1)',
            'rgba(255, 206, 86, 1)',
            'rgba(255, 206, 86, 1)',
            'rgba(255, 206, 86, 1)'
          ],
          borderWidth: 1
        }, {
          label: 'Jacobi',
          data: [0.02279112, 0.03222227999999999, 0.16908905000000002, 0.31473802, 2.3812020900000004, 20.925418649999997, 169.32787048000003, 2884.9801644000004],
          backgroundColor: [
            'rgba(255, 99, 132, 0.2)',
            'rgba(255, 99, 132, 0.2)',
            'rgba(255, 99, 132, 0.2)',
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
            'rgba(255, 99, 132, 1)',
            'rgba(255, 99, 132, 1)',
            'rgba(255, 99, 132, 1)',
            'rgba(255, 99, 132, 1)'
          ],
          borderWidth: 1
        }, {
          label: 'SOR',
          data: [0.6680628499999999, 2.21912192, 1.7844638499999996, 6.985739589999998, 16.335796760000004, 74.18939488, 490.06560447, 3519.752066430001],
          backgroundColor: [
            'rgba(54, 162, 235, 0.2)',
            'rgba(54, 162, 235, 0.2)',
            'rgba(54, 162, 235, 0.2)',
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
            'rgba(54, 162, 235, 1)',
            'rgba(54, 162, 235, 1)',
            'rgba(54, 162, 235, 1)',
            'rgba(54, 162, 235, 1)'
          ],
          borderWidth: 1
        }, {
          label: 'GMRES',
          data: [0.07192015999999998, 0.08203558999999999, 0.29359583, 0.55768051, 2.3815754000000005, 5.7097517700000004, 29.447817290000003, 235.42211146000002],
          backgroundColor: [
            'rgba(49, 199, 35, 0.2)',
            'rgba(49, 199, 35, 0.2)',
            'rgba(49, 199, 35, 0.2)',
            'rgba(49, 199, 35, 0.2)',
            'rgba(49, 199, 35, 0.2)',
            'rgba(49, 199, 35, 0.2)',
            'rgba(49, 199, 35, 0.2)',
            'rgba(49, 199, 35, 0.2)'
          ],
          borderColor: [
            'rgba(49, 199, 35, 1)',
            'rgba(49, 199, 35, 1)',
            'rgba(49, 199, 35, 1)',
            'rgba(49, 199, 35, 1)',
            'rgba(49, 199, 35, 1)',
            'rgba(49, 199, 35, 1)',
            'rgba(49, 199, 35, 1)',
            'rgba(49, 199, 35, 1)'
          ],
          borderWidth: 1
        }]
      },
      options: {
        title: {
          display: true,
          text: 'Temps de résolution (ms) pour chaque méthode pour différentes tailles de matrice ',
          fontsize: 12
        },
        scales: {
          yAxes: [{
            type: 'logarithmic',
            text: 'Temps de résolution en ms',
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

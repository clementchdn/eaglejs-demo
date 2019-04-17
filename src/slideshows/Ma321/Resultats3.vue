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
      type: 'bar',
      title: {
        text: 'Nombre d\'itérations pour différentes tailles de matrice avec une précision de 1e-9'
      },
      data: {
        labels: ['5', '10', '25', '50', '100', '250', '500', '1000'],
        datasets: [{
          label: 'Gauss-Seidel',
          data: [3.0, 3.0, 3.02, 3.13, 3.6, 4.0, 4.0, 4.0],
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
          data: [3.01, 3.04, 3.08, 3.45, 3.83, 4.01, 4.0, 4.03],
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
          data: [199.47, 374.77, 151.66, 218.43, 249.06, 195.89, 467.0, 193.24],
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
          data: [1.0, 1.0, 1.0, 1.0, 1.0, 1.0, 1.0, 1.0],
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
          text: 'Nombre d\'itérations pour différentes tailles de matrice avec une précision de 1e-9',
          fontsize: 12
        },
        scales: {
          yAxes: [{
            type: 'linear',
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

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
        labels: ['5', '10', '25', '50', '100'],
        datasets: [{
          label: 'Gauss-Seidel',
          data: [0.597175622, 1.2809175959999999, 4.125076545999999, 14.555804022, 70.933127064],
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
          data: [0.44883063599999995, 0.8332638000000001, 1.910239056, 4.991868437999999, 22.763995334],
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
          data: [17.524580936, 23.8681652, 39.30653805199999, 71.473159542, 92.31667759599999],
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
          text: 'Temps de résolution (ms) pour chaque méthode pour différentes tailles de matrice ',
          fontsize: 12
        },
        scales: {
          yAxes: [{
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

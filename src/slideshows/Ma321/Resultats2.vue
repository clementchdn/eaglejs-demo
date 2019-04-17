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
        labels: ['5', '10', '25', '50', '100', '250', '500', '1000'],
        datasets: [{
          label: 'Gauss-Seidel',
          data: [3.3068293316999995e-08, 1.4770604774999997e-07, 8.914919555635289e-07, 1.9795882407759827e-06, 1.8213669936318597e-06, 7.524426529800001e-11, 5.439052230399999e-10, 3.09270270896e-08],
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
          data: [8.644069823943999e-08, 2.674376213541597e-07, 1.485012695276361e-06, 2.0891805225800864e-06, 1.074485912287744e-06, 1.782518328046e-08, 2.6413080118100003e-08, 1.7218445439300003e-07],
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
          data: [6.954154895e-06, 7.236338652999999e-06, 6.8032887024e-06, 7.301168539999999e-06, 7.5186323200000015e-06, 6.831551701000002e-06, 7.309609007999999e-06, 6.8870147760000005e-06],
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
          data: [1.08745758836e-18, 6.680449917799999e-19, 3.4807094502999997e-19, 3.1170160824e-19, 1.7686883275999997e-19, 1.109874579616e-19, 8.8770435247e-20, 6.306824651e-20],
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
          text: 'Erreurs pour des matrices de tailles différentes pour chaque méthode avec une précision de 1e-5 ',
          fontsize: 12
        },
        scales: {
          yAxes: [{
            type: 'logarithmic',
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

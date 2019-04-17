<template lang='pug'>
eg-transition(enter="bounceInRight" leave="slideOutLeft")
  .subslide
    .center(style="width:80%; height: 50%; margin-top: 1em")
      <input type='file' id='fileInput' @change="onFileChange"/>
      #container(style='height: 600px; width: 900px;')
</template>

<script src="https://code.highcharts.com/highcharts.js"></script>
<script src="https://code.highcharts.com/highcharts-3d.js"></script>
<script src="https://code.highcharts.com/modules/exporting.js"></script>
<script src="https://code.highcharts.com/modules/export-data.js"></script>
<script>
var Highcharts = require('highcharts')
require('highcharts/highcharts-3d')(Highcharts)
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
      file: '',
      content: '',
      errors: [],
      times: [],
      iterations: []
    }
  },
  methods: {
    onFileChange (e) {
      this.readSingleFile(e)
    },
    readSingleFile (e) {
      const files = e.target.files || e.dataTransfer.files
      if (files.length > 0) var file = files[0]
      console.log(file)
      var reader = new FileReader()
      reader.readAsText(file, 'UTF-8')
      var errors = []
      var times = []
      var iterations = []
      var points = []
      reader.onloadend = function (evt) {
        this.content = evt.target.result
        var lines = this.content.split('\r')
        var rows = []
        for (var i = 0; i <= lines.length - 2; i += 2) {
          rows.push(lines[i].split(','))
        }
        for (var k = 0; k <= rows.length - 1; k++) {
          errors.push(parseFloat(rows[k][0]))
          times.push(parseFloat(rows[k][1]))
          iterations.push(parseInt(rows[k][2]))
        }
        for (var l =0; l <= errors.length - 2; l++) {
          var point = []
          point.push(errors[l], times[l], iterations[l])
          points.push(point)
        }
        console.log(Math.min.apply(null, times))
        console.log('POINTS', points)
        var chart = new Highcharts.Chart({
          chart: {
              renderTo: 'container',
              margin: 100,
              type: 'scatter3d',
              animation: false,
              options3d: {
                  enabled: true,
                  alpha: 10,
                  beta: 30,
                  depth: 250,
                  viewDistance: 5,
                  fitToPlot: false,
                  frame: {
                      bottom: { size: 1, color: 'rgba(0,0,0,0.02)' },
                      back: { size: 1, color: 'rgba(0,0,0,0.04)' },
                      side: { size: 1, color: 'rgba(0,0,0,0.06)' }
                  }
              }
          },
          title: {
              text: 'Mesures avec des matrices de taille 100x100 avec une précision de 1e-5 pour la méthode' + file.name
          },
          subtitle: {
              text: 'Click and drag the plot area to rotate in space'
          },
          plotOptions: {
              scatter: {
                  width: 10,
                  height: 10,
                  depth: 10
              }
          },
          yAxis: {
              min: Math.min.apply(null, times) - (Math.min.apply(null, times)/10),
              max: Math.max.apply(null,times) + (Math.max.apply(null, times)/10),
              title:{
                text: 'Temps de résolution en ms'
              }
          },
          xAxis: {
              min: Math.min.apply(null, errors) - (Math.min.apply(null, errors)/10),
              max: Math.max.apply(null, errors) + (Math.max.apply(null, errors)/10),
              title: {
                text: 'Erreurs'
              },
              gridLineWidth: 1
          },
          zAxis: {
              min: Math.min.apply(null, iterations) - (Math.min.apply(null, iterations)/10),
              max: Math.max.apply(null, iterations) + (Math.max.apply(null, iterations)/10),
              title: {
                text: 'Nombre d\'itérations'
              },
              showFirstLabel: true
          },
          legend: {
              enabled: false
          },
          series: [{
              name: 'Reading',
              colorByPoint: true,
              data: points
          }]
        });
        (function (H) {
          function dragStart(eStart) {
              eStart = chart.pointer.normalize(eStart);

              var posX = eStart.chartX,
                  posY = eStart.chartY,
                  alpha = chart.options.chart.options3d.alpha,
                  beta = chart.options.chart.options3d.beta,
                  sensitivity = 5,  // lower is more sensitive
                  handlers = [];

              function drag(e) {
                  // Get e.chartX and e.chartY
                  e = chart.pointer.normalize(e);

                  chart.update({
                      chart: {
                          options3d: {
                              alpha: alpha + (e.chartY - posY) / sensitivity,
                              beta: beta + (posX - e.chartX) / sensitivity
                          }
                      }
                  }, undefined, undefined, false);
              }

              function unbindAll() {
                  handlers.forEach(function (unbind) {
                      if (unbind) {
                          unbind();
                      }
                  });
                  handlers.length = 0;
              }

              handlers.push(H.addEvent(document, 'mousemove', drag));
              handlers.push(H.addEvent(document, 'touchmove', drag));

              handlers.push(H.addEvent(document, 'mouseup', unbindAll));
              handlers.push(H.addEvent(document, 'touchend', unbindAll));
          }
          H.addEvent(chart.container, 'mousedown', dragStart);
          H.addEvent(chart.container, 'touchstart', dragStart);
        }(Highcharts));
      }
    }
  },
  mounted: function () {
    Highcharts.setOptions({
      colors: Highcharts.getOptions().colors.map(function (color) {
          return {
              radialGradient: {
                  cx: 0.4,
                  cy: 0.3,
                  r: 0.5
              },
              stops: [
                  [0, color],
                  [1, Highcharts.Color(color).brighten(-0.2).get('rgb')]
              ]
          };
      })
    })
  }
}
</script>
<style>
#container {
    height: 400px;
    min-width: 310px;
    max-width: 800px;
    margin: 0 auto;
}
</style>

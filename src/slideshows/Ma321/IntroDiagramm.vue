<template lang="pug">
eg-transition(enter="bounceInRight" leave="slideOutLeft")
  .subslide
    .center(style="width:80%; height: 50%; margin-top: 2em")
      #tester
</template>
<script src="https://code.highcharts.com/highcharts.js"></script>
<script src="https://code.highcharts.com/modules/venn.js"></script>
<script src="https://code.highcharts.com/modules/exporting.js"></script>
<script>

import eagle from 'eagle.js'
var Plotly = require('plotly.js-dist')
var Highcharts = require('highcharts')
var venn = require('highcharts/modules/venn')
venn(Highcharts)
export default {
  props: {
    steps: { default: 17 },
    nomdumec: { default: 'Inconnu' }
  },
  components: {
  },
  /*data: function () {
    return {
      tester: null
    }
  },*/
  mixins: [eagle.slide],
  mounted: function () {
    Highcharts.chart('tester', {
        series: [{
            type: 'venn',
            name: 'The Unattainable Triangle',
            data: [{
                sets: ['Esthétique'],
                value: 2
            }, {
              sets: ['Mathématique'],
                value: 2
            }, {
                sets: ['Simple'],
                value: 2
            }, {
                sets: ['Mathématique', 'Esthétique'],
                value: 1,
                name: 'Eaglejs'
            }, {
                sets: ['Esthétique', 'Simple'],
                value: 1,
                name: 'Powerpoint'
            }, {
                sets: ['Mathématique', 'Simple'],
                value: 1,
                name: 'Beamer'
            }, {
                sets: ['Mathématique', 'Simple', 'Esthétique'],
                value: 1,
                name: 'Inexistant ?'
            }]
        }],
        title: {
            text: 'Comment présenter notre soutenance ?'
        }
    });
    /*Highcharts.chart('tester', {
        series: [{
            type: 'venn',
            name: 'Le prof de maths parfait',
            data: [{
                sets: ['Intéressant'],
                value: 2
            }, {
              sets: ['Bon en maths'],
                value: 2
            }, {
                sets: ['Sait coder'],
                value: 2
            }, {
                sets: ['Sait coder', 'Bon en maths'],
                value: 1,
                name: 'M. Peschard'
            }, {
                sets: ['Intéressant', 'Bon en maths'],
                value: 1,
                name: 'M. Ciril'
            }, {
                sets: ['Sait coder', 'Intéressant'],
                value: 1,
                name: 'M. Maltese'
            }, {
                sets: ['Intéressant', 'Bon en maths', 'Sait coder'],
                value: 1,
                name: this.nomdumec
            }]
        }],
        title: {
            text: 'Le prof de maths parfait'
        }
    });*/
  }
}

</script>
<style lang='scss' scoped>
.eg-slide, .subslide {
  height: 100%;
  .eg-slide-content {
    #container {
      min-width: 320px;
      max-width: 600px;
      height: 400px;
      margin: 0 auto;
    }
    //display: grid;
    grid-row-gap: 10px;
    height: 100%;

    #objectifs {
      display: grid;
    }
    .subgauche {
      display: grid;
      margin: auto;
      grid-column: 1;
      grid-row-gap: 15px;
      #g1 {grid-row: 1; font-size: 25px;}
      #g2 {grid-row: 2; margin:auto; font-size: 25px;}
    }
    .subdroite {
      display: grid;
      margin: auto;
      grid-column: 2;
      grid-row-gap: 15px;
      #d1 {grid-row: 1;}
      #d2 {grid-row: 2; margin: auto}
    }
    #awesome-slideshow {
      position: relative;
      margin: 0 auto;
      width: 16em;
      height: 9em;
    }
  }
}
</style>

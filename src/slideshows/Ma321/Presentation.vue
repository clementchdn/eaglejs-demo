<template lang="pug">
#Presentation
    slide(steps="3" :mouseNavigation='false')
        h2.align-center Optimisation des méthodes itératives pour la résolution de systèmes d'équations linéaires
        h3.align-center(v-if="step >= 2") Quel est-ton nom ?
        .align-center(v-if="step >= 2" style="margin-bottom: 0; ")
          input.align-center(type="text" name="" value="" v-model="nomdumec")
          p.align-center(v-if="nomdumec !== '' " style='margin-bottom: 5px;') Bonjour {{nomdumec}}
        introdiagram(:nomdumec='nomdumec' v-if="step === 3" style="margin-top: -50px;")
    krylov(:nomdumec='nomdumec', :mouseNavigation='false', :demo1='false', :demo2='false')
    richardson(:nomdumec='nomdumec', :mouseNavigation='false')
    sor(:nomdumec='nomdumec' :mouseNavigation='false')
    slide(:mouseNavigation='false' steps="8")
      p Titre de mes slides
      resultats1(v-if="step === 1")
      resultats2(v-if="step === 3")
      resultats3(v-if="step === 5")
      test3D(v-if="step === 7")
</template>
<script>
import eagle from 'eagle.js'
import Vue from 'vue'
import ToggleButton from 'vue-js-toggle-button'
Vue.use(ToggleButton)

export default {
  mixins: [eagle.slideshow],
  infos: {
    title: 'Presentation Ma321',
    description: 'Présentation de notre mémoire',
    path: 'Ma321'
  },
  components: {
    'introdiagram': require('./IntroDiagramm').default,
    'partie2': require('./Partie2').default,
    'resultats1': require('./Resultats1').default,
    'resultats2': require('./Resultats2').default,
    'resultats3': require('./Resultats3').default,
    'richardson': require('./Richardson').default,
    'test3D': require('./test3D').default,
    'sor': require('./SOR').default,
    'krylov': require('./Krylov').default
  },
  data: function () {
    return {
      nomdumec: '',
      demo1: false,
      demo2: false
    }
  },
  methods: {
    afficherNom () {
      console.log(this.nomdumec)
    },
    message: function (name) {
      return {
        'baby bunnies': 'Yeeeeah my favorite too !',
        'fluffy puppies': 'Wow so original.',
        'funny kitties': 'Good for you ' + this.username + '.',
        'Theming': 'Ok ' + this.username + ', whatever.',
        'Slide reuse': 'Seriously ' + this.username + ' you <em>want</em> to see this.',
        'Interactivity': 'Well that\'s this slide, ' + this.username +
                         '. <br /> A bit too late to unsee it, heh ?'
      }[name]
    }
  }
}
</script>

<style lang='scss'>
@import 'node_modules/eagle.js/dist/themes/agrume/agrume';
* {
  p, math {
    font-size: 25px;
  }
  .subslide {
    .align-center {
        text-align: center;
    }
    .bordered {
      border: 1px solid black;
      padding: 6px;
    }
    .center {
      margin-left: auto;
      margin-right: auto;
    }
  }
  .small-margin-left {
      margin-left: 10px;
  }
  .small-marin-right {
      margin-right: 10px;
  }
  ul, li {
      font-size: 25px;
  }
}
#Presentation {
  padding: 5vh;
  height: 100%;
  .frontpage {
    img {
      height: 7em;
    }
    img.control-schema {
      width: 8em;
      height: 3em;
    }
  }
  .center {
      margin-left: auto;
      margin-right: auto;
  }
  .align-center{
    text-align: center;
  }
  .heart {
    width: 1em;
    height: 0.8em;
    margin-left: 0.1em;
    margin-right: 0.1em;
    background-image: url('../introducing-eagle/assets/heart.svg');
    background-position: center center;
    background-repeat:  no-repeat;
    background-size: contain;
  }

  .quarter {
    text-align: center;
    p {
      margin-top: 0;
      text-align: center;
    }
    h4 {
      margin-top: 0;
      margin-bottom: 0
    }
  }
  .boredYet {
    p {
      margin-bottom: 0.3em;
      margin-top: 1.3em;
    }
    .button {
      border: none;
    }
    .button.prev {
      float: left;
    }
    .button.next {
      float: right;
    }
  }
  img.computerkid {
    height: 6.5em;
  }

  a {
    color: black;
  }

  .parentWindow {
    border: solide 1px red;
  }
}
</style>

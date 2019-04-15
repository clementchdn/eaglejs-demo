<template lang="pug">
#Presentation
    slide(steps="2" :mouseNavigation='false')
        h2.align-center Optimisation des méthodes itératives pour la résolution de systèmes d'équations linéaires
        h3.align-center(v-if="step >= 2") Quel est-ton nom ?
        .align-center(v-if="step >=2")
          input.align-center(type="text" name="" value="" v-model="nomdumec")
          p.align-center(v-if="nomdumec !== '' ") Bonjour {{nomdumec}}
    krylov(:nomdumec='nomdumec', :mouseNavigation='false', :demo1='false', :demo2='false')
    richardson(:nomdumec='nomdumec', :mouseNavigation='false')
    slide(:mouseNavigation='false')
      .align-center
        <math class="align-center">
          <mtable>
          <mtr>
          <mtd>
          <mspace/>
          </mtd>
          <mtd columnalign="left">
          <mstyle displaystyle="true">
          <munder>
          <mrow>
          <munder accentunder="true">
          <mrow>
          <mo rspace="0.3em" lspace="0em" stretchy="true" fence="true" form="prefix">(</mo>
          <mtable class="m-pmatrix">
          <mtr>
          <mtd>
          <mo>-</mo>
          <mn>3</mn>
          </mtd>
          <mtd>
          <mn>2</mn>
          </mtd>
          </mtr>
          <mtr>
          <mtd>
          <mn>1</mn>
          </mtd>
          <mtd>
          <mo>-</mo>
          <mn>4</mn>
          </mtd>
          </mtr>
          </mtable>
          <mo rspace="0em" lspace="0.3em" stretchy="true" fence="true" form="postfix">)</mo>
          </mrow>
          <mo stretchy="true">&UnderBrace;</mo>
          </munder>
          </mrow>
          <mi>A</mi>
          </munder>
          </mstyle>
          <mstyle displaystyle="true">
          <munder>
          <mrow>
          <munder accentunder="true">
          <mrow>
          <mo rspace="0.3em" lspace="0em" stretchy="true" fence="true" form="prefix">(</mo>
          <mtable class="m-pmatrix">
          <mtr>
          <mtd>
          <mi>x</mi>
          </mtd>
          </mtr>
          <mtr>
          <mtd>
          <mi>y</mi>
          </mtd>
          </mtr>
          </mtable>
          <mo rspace="0em" lspace="0.3em" stretchy="true" fence="true" form="postfix">)</mo>
          </mrow>
          <mo stretchy="true">&UnderBrace;</mo>
          </munder>
          </mrow>
          <mi>x</mi>
          </munder>
          </mstyle>
          <mo>=</mo>
          <mstyle displaystyle="true">
          <munder>
          <mrow>
          <munder accentunder="true">
          <mrow>
          <mo rspace="0.3em" lspace="0em" stretchy="true" fence="true" form="prefix">(</mo>
          <mtable class="m-pmatrix">
          <mtr>
          <mtd>
          <mn>1</mn>
          </mtd>
          </mtr>
          <mtr>
          <mtd>
          <mo>-</mo>
          <mn>7</mn>
          </mtd>
          </mtr>
          </mtable>
          <mo rspace="0em" lspace="0.3em" stretchy="true" fence="true" form="postfix">)</mo>
          </mrow>
          <mo stretchy="true">&UnderBrace;</mo>
          </munder>
          </mrow>
          <mi>b</mi>
          </munder>
          </mstyle>
          </mtd>
          <mtd columnalign="right">
          <mtext id="">(1)</mtext>
          <mspace/>
          </mtd>
          </mtr>
          </mtable>
        </math>
    slide(:mouseNavigation='false')
      .align-center
        <math>
          <mtable>
          <mtr>
          <mtd rowspan="3">
          </mtd>
          <mtd columnalign="right">
          <mi>a</mi>
          </mtd>
          <mtd columnalign="left">
          <mo>=</mo>
          <mi>b</mi>
          </mtd>
          <mtd rowspan="3">
          </mtd>
          <mtd columnalign="right">
          <mi>A</mi>
          </mtd>
          <mtd columnalign="left">
          <mo>=</mo>
          <mi>B</mi>
          </mtd>
          <mtd rowspan="3">
          </mtd>
          <mtd columnalign="right">
          <mi>x</mi>
          </mtd>
          <mtd columnalign="left">
          <mo>=</mo>
          <mi>y</mi>
          <mo>+</mo>
          <mi>z</mi>
          </mtd>
          <mtd columnalign="right">
          <mtext id="align-eq1">(1.6)</mtext>
          </mtd>
          </mtr>
          <mtr>
          <mtd columnalign="right">
          <mi>c</mi>
          <mi>d</mi>
          </mtd>
          <mtd columnalign="left">
          <mo>=</mo>
          <mi>e</mi>
          <mi>f</mi>
          </mtd>
          <mtd columnalign="right">
          <mi>C</mi>
          <mi>D</mi>
          </mtd>
          <mtd columnalign="left">
          <mo>=</mo>
          <mi>E</mi>
          <mi>F</mi>
          </mtd>
          <mtd columnalign="right">
          <mi>k</mi>
          </mtd>
          <mtd columnalign="left">
          <mo>=</mo>
          <mi>m</mi>
          </mtd>
          <mtd columnalign="right">
          <mtext id="align-eq2">(1.7)</mtext>
          </mtd>
          </mtr>
          <mtr>
          <mtd columnalign="right">
          <mi>g</mi>
          <mo>+</mo>
          <mi>h</mi>
          </mtd>
          <mtd columnalign="left">
          <mo>=</mo>
          <mi>i</mi>
          <mo>+</mo>
          <mi>j</mi>
          </mtd>
          <mtd columnalign="right">
          <mi>G</mi>
          <mo>+</mo>
          <mi>H</mi>
          </mtd>
          <mtd columnalign="left">
          <mo>=</mo>
          <mi>I</mi>
          <mo>+</mo>
          <mi>J</mi>
          </mtd>
          <mtd columnalign="right">
          <mi>n</mi>
          <mi>q</mi>
          </mtd>
          <mtd columnalign="left">
          <mo>=</mo>
          <mi>r</mi>
          <mi>s</mi>
          </mtd>
          <mtd columnalign="right">
          <mtext id="align-eq3">(1.8)</mtext>
          </mtd>
          </mtr>
          </mtable>
        </math>
    slide(:mouseNavigation='false' steps="7")
      p Titre de mes slides
      resultats1(v-if="step === 1")
      resultats2(v-if="step === 3")
      resultats3(v-if="step === 5")
      resultats4(v-if="step === 7")
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
    'partie2': require('./Partie2').default,
    'resultats1': require('./Resultats1').default,
    'resultats2': require('./Resultats2').default,
    'resultats3': require('./Resultats3').default,
    'resultats4': require('./Resultats4').default,
    'richardson': require('./Richardson').default,
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

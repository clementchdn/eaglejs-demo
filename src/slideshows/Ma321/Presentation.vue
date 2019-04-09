<template>
<div id="Presentation">
    <slide :steps="2" :mouseNavigation='false'>
        <h1 class="center"> Optimisation des méthodes itératives pour la résolution de systèmes d'équations linéaires </h1>
        <h2 class="center" v-if="step >= 2"> Quel est-ton nom ?</h2>
        <div class="center" v-if="step >=2">
          <input class="center" type="text" name="" value="" v-model="nomdumec"/>
          <p class="center" v-if="nomdumec !== '' ">Bonjour {{nomdumec}}</p>
        </div>

    </slide>
    <slide :mouseNavigation='false' :steps="7">
        <p class="center"> Ok {{nomdumec}}, je vous montre la table des matières ?</p>
        <div class="center">
            <toggle-button v-model="tdm" color="#82C7EB" :sync="true" :labels="true"/>
        </div>

        <div v-if="tdm" class="tabledesmatieres subslide">
            <ol v-if="step >= 1">
                <li v-if="step >= 1"> Introduction </li>
                <li>
                  <ol v-if="step >=2"> Présentation des méthodes itératives classiques <div> <toggle-button v-model="slides.Partie2" colors="#daf9c6" :sync="true" :labels="true"/></div>
                    <li v-if="step >=3"> Présentation générale des méthodes</li>
                    <li v-if="step >=4"> Méthodes classiques</li>
                  </ol>
                </li>
                <li>
                  <ol v-if="step >=5"> Une nouvelle méthode : Richardson
                    <li v-if="step >=6"> Présentation de la méthodes</li>
                    <li v-if="step >=7"> Étude de convergence sur un exemple</li>
                  </ol>
                </li>
            </ol>
        </div>
    </slide>

    <partie2></partie2>

    <slide>
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
    </slide>
</div>
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
    'partie2': require('./Partie2').default
  },
  data: function () {
    return {
      nomdumec: '',
      tdm: false,
      username: 'Tracy',
      preloadedImages: {
        computerKid: 'https://i.imgur.com/AAlntwU.gif',
        youRightNow: 'https://i.imgur.com/DFBTj0a.gif',
        bretagne: 'https://i.imgur.com/rYkJ6I8.jpg',
        forrestRoad: 'https://i.imgur.com/hxTMFZW.jpg',
        starrySky: 'https://i.imgur.com/yO2ivoD.jpg',
        cityBokeh: 'https://i.imgur.com/kmmHith.jpg',
        darkWoods: 'https://i.imgur.com/FL9mwpd.jpg',
        pushButton: 'https://i.imgur.com/KaAyvZ5.gif'
      }
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
#Presentation {
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

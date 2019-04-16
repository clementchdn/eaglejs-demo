<template lang="pug">
eg-transition(enter='slideInRight', v-if='step <= 17')
  .eg-slide(v-if='active && step === 1')
    .eg-slide-content
      .align-center(style='margin-top: 15%;')
        h2 Successive Over Relaxation (SOR)
  .subslide(v-if='active && step > 1 && step <=4')
    .eg-slide-content
      h2(style='margin-bottom: 10%;') Nécessité de trouver une autre méthode
      .align-center(v-if='step >=2')
        p Lorsque le calcul des valeurs propres est difficile, le choix de <math><mrow><mi>&gamma;</mi></mrow></math> l'est aussi
      p(v-if='step >=3' style='color:orange;') Objectif :
      .align-center(v-if='step >=3 ')
        p Avoir une méthode qui ne nécessite pas le calcul de valeurs propres
      p(v-if='step >=4' style='color:orange;') Solution :
      .align-center(v-if='step >=4')
        p Successive over-relaxation (SOR)
  .subslide(v-if='active && step > 4 && step <= 11')
    .eg-slide-content
      h2 Principe
      .align-center
        p(v-if='step >= 5') Décomposition de la matrice <math><mi>A</mi></math> :
        <math v-if='step >= 6'><mrow><mi>A</mi><mo>=</mo><mi>M</mi><mo>-</mo><mi>N</mi></mrow></math>
        <div v-if='step >= 7' style='font-size:25px;'>
        <math v-if='step >= 7'><mrow><mi>M</mi><mo>=</mo><mfrac linethickness="1"><mn>1</mn><mi>&omega;</mi></mfrac><mi>D</mi><mo>-</mo><mi>E</mi></mrow></math> et <math v-if='step >= 7'><mrow><mi>N</mi><mo>=</mo><mrow><mo form="prefix">(</mo><mfrac linethickness="1"><mn>1</mn><mi>&omega;</mi></mfrac><mo>-</mo><mn>1</mn><mo form="postfix">)</mo></mrow><mi>D</mi><mo>+</mo><mi>F</mi></mrow></math></div>
      p(v-if='step >= 8' style='margin: 3% 30% 1% 30%;') Avec :
      ul(v-if='step >= 8' style='margin: 0 33%')
        li(v-if='step >= 8') <math><mrow><mi>D</mi></mrow></math> : diagonale,
        li(v-if='step >= 9') <math><mrow><mi>E</mi></mrow></math> : triangulaire inférieure,
        li(v-if='step >= 10') <math><mrow><mi>F</mi></mrow></math> : triangulaire supérieure,
        li(v-if='step >= 11') <math><mrow><mi>&omega;</mi></mrow></math> : paramètre de relaxation, réel non nul
  .subslide(v-if='active && step > 11 && step <=15 ')
    .eg-slide-content
      h2 Caractéristiques et intérêt
      .align-center
        <math><mrow><msup><mi>X</mi><mrow><mi>k</mi><mo>+</mo><mn>1</mn></mrow></msup><mo>=</mo><mi>B</mi><msup><mi>X</mi><mi>k</mi></msup><mo>+</mo><mi>C</mi></mrow></math>
      ul(v-if='step >= 12' style='margin: 3% 33% 0 33%')
        li(v-if='step >= 12') <math><mrow><mi>B</mi><mo>=</mo><msup><mi>M</mi><mn>-1</mn></msup><mi>N</mi></mrow></math> la matrice d'itération.
        li(v-if='step >= 12') <math><mrow><mi>C</mi><mo>=</mo><msup><mi>M</mi><mn>-1</mn></msup><mi>b</mi></mrow></math>
      .align-center(v-if='step >= 13')
        p(v-if='step >= 13') Choix facile de <math><mrow><mi>&omega;</mi></mrow></math> pour assurer la convergence
        p(v-if='step >= 14') Condition nécessaire et suffisante de convergence : <math><mrow><mi>&omega;</mi><mo>&isin;</mo><mo form="postfix">]</mo><mn>0</mn><mo>;</mo><mn>2</mn><mo form="prefix">[</mo></mrow></math>
        p(v-if='step >= 15') Théorème de Kahan et théorème d'Ostrowski-Reich
  .subslide(v-if='active && step === 16')
    .eg-slide-content
      h2 Limites de la méthodes
      .align-center(style='margin-top: 10%')
        ul
          li Faible vitesse de convergence
          li Choix de <math><mrow><msub><mi>&omega;</mi><mrow><mi>o</mi><mi>p</mi><mi>t</mi><mi>i</mi><mi>m</mi><mi>a</mi><mi>l</mi></mrow></msub></mrow></math> difficile et très situationnel
</template>

<script>
import eagle from 'eagle.js'
export default {
  props: {
    steps: { default: 17 },
    nomdumec: { default: 'Inconnu' }
  },
  components: {
  },
  mixins: [eagle.slide]
}
</script>
<style lang='scss' scoped>
.eg-slide, .subslide {
  height: 100%;
  .eg-slide-content {
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

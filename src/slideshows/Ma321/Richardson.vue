<template lang="pug">
eg-transition(enter='slideInRight', v-if='step <=13')
  .eg-slide(v-if='active && step <= 3')
    .eg-slide-content
      h2 Les limites de Jacobi et Gauss-Seidel
      ul(v-if='step >= 2')
        li(v-if='step >= 2') Problème de fiabilité avec Jacobi et Gauss-Seidel au niveau de la convergence.
        li(v-if='step >= 3') Nécessité de garantir une convergence.

  .subslide(v-if='step > 3 && step <= 9')
    .eg-slide-content
      h2 Garantie d'une convergence
      eg-transition(enter='lightSpeedIn' v-if='step >= 5')
        h4.align-center Méthode de Richardson
      .align-center(v-if='step >= 6')
        <math>
            <mrow>
            <mi>A</mi>
            <mi>X</mi>
            <mo>=</mo>
            <mi>b</mi>
            <mo>&hArr;</mo>
            <mi>P</mi>
            <mi>X</mi>
            <mo>=</mo>
            <mrow>
            <mo form="prefix">(</mo>
            <mi>P</mi>
            <mo>-</mo>
            <mi>A</mi>
            <mo form="postfix">)</mo>
            </mrow>
            <mi>X</mi>
            <mo>+</mo>
            <mi>b</mi>
            </mrow></math>
      .align-center(v-if='step >= 7')
         p(v-if='step >= 7') Avec <math><mrow><mi>P</mi><mo>=</mo><mi>&beta;</mi><mi>I</mi></mrow></math>, <math><mrow><mi>&beta;</mi><mo>&isin;</mo><msup><mi>&Ropf;</mi><mo>*</mo></msup></mrow></math>
         <math v-if='step >= 8'>
          <mrow>
          <mo>&hArr;</mo>
          <msup>
          <mi>X</mi>
          <mrow>
          <mi>k</mi>
          <mo>+</mo>
          <mn>1</mn>
          </mrow>
          </msup>
          <mo>=</mo>
          <mrow>
          <mo form="prefix">(</mo>
          <mi>I</mi>
          <mo>-</mo>
          <mi>&gamma;</mi>
          <mi>A</mi>
          <mo form="postfix">)</mo>
          </mrow>
          <msup>
          <mi>X</mi>
          <mi>k</mi>
          </msup>
          <mo>+</mo>
          <mi>&gamma;</mi>
          <mi>b</mi>
          </mrow>
         </math>
         p(v-if='step >= 9 ') où <math>
          <mrow>
          <mi>&gamma;</mi>
          <mo>=</mo>
          <mfrac linethickness="1">
          <mn>1</mn>
          <mi>&beta;</mi>
          </mfrac>
          </mrow></math>
  .subslide(v-if='step > 9 && step <= 14')
    .eg-slide-content
      h2 Méthode de Richardson
      p Modèle :
      .align-center(v-if='step >= 11')
        <math>
            <mrow>
            <msup>
            <mi>X</mi>
            <mrow>
            <mi>k</mi>
            <mo>+</mo>
            <mn>1</mn>
            </mrow>
            </msup>
            <mo>=</mo>
            <mi>R</mi>
            <msup>
            <mi>X</mi>
            <mi>k</mi>
            </msup>
            <mo>+</mo>
            <mi>K</mi>
            </mrow>
        </math>
      p(v-if='step >=12') Caractéristiques :
      ul(v-if='step >=12')
        li(v-if='step >=12') Matrice d'itération : <math><mrow><mi>R</mi><mo>=</mo><mrow><mo form="prefix">(</mo><mi>I</mi><mo>-</mo><mi>&gamma;</mi><mi>A</mi><mo form="postfix">)</mo></mrow></mrow></math>
        li(v-if='step >=13') <math><mrow><mi>K</mi><mo>=</mo><mi>&gamma;</mi><mi>b</mi></mrow></math>
</template>

<script>
import eagle from 'eagle.js'
export default {
  props: {
    steps: { default: 14 },
    nomdumec: { default: 'Inconnu' }
  },
  components: {
  },
  mixins: [eagle.slide]
}
</script>
<style lang='scss' scoped>
.eg-slide {
  .eg-slide-content {
    display: grid;
    grid-row-gap: 10px;

    #subgauche {
        grid-column: 1;
    }

    #subdroite {
      grid-column: 2;
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

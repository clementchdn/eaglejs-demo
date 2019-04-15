<template lang="pug">
eg-transition(enter='slideInRight')
  .eg-slide(v-if='active && step <= 3')
    .eg-slide-content
      h2 Les limites de Jacobi et Gauss-Seidel
      ul(v-if='step >= 2')
        li(v-if='step >= 2') Problème de fiabilité avec Jacobi et Gauss-Seidel au niveau de la convergence.
        li(v-if='step >= 3') Nécessité de garantir une convergence.

  .subslide(v-if='step > 3 && step <= 8')
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
         p Avec
         <math>
          <mtable class="m-align-starred">
          <mtr>
          <mtd rowspan="2">
          <mspace/>
          </mtd>
          <mtd columnalign="right">
          <mi>P</mi>
          </mtd>
          <mtd columnalign="left">
          <mo>=</mo>
          <mi>&beta;</mi>
          <mi>I</mi>
          <mo>,</mo>
          <mi>&beta;</mi>
          <mo>&isin;</mo>
          <msup>
          <mi>&Ropf;</mi>
          <mo>*</mo>
          </msup>
          </mtd>
          <mtd columnalign="right">
          <mspace/>
          </mtd>
          </mtr>
          <mtr>
          <mtd columnalign="right">
          <mo>&hArr;</mo>
          <msup>
          <mi>X</mi>
          <mrow>
          <mi>k</mi>
          <mo>+</mo>
          <mn>1</mn>
          </mrow>
          </msup>
          </mtd>
          <mtd columnalign="left">
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
          </mtd>
          <mtd columnalign="right">
          <mspace/>
          </mtd>
          </mtr>
          </mtable>
         </math>
</template>

<script>
import eagle from 'eagle.js'
export default {
  props: {
    steps: { default: 12 },
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

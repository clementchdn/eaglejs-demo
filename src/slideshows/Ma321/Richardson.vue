<template lang="pug">
eg-transition(enter='slideInRight', v-if='step <= 21')
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
  .subslide(v-if='step > 14 && step <= 17')
    .eg-slide-content
      h2 Intérêt de la méthode
      p La condition de convergence reste inchangée
      .align-center(v-if='step >= 15')
        <math>
          <mrow>
          <mi>&rho;</mi>
          <mrow>
          <mo form="prefix">(</mo>
          <mi>R</mi>
          <mo form="postfix">)</mo>
          </mrow>
          <mo>&lt;</mo>
          <mn>1</mn>
          </mrow>
        </math>
      p(v-if='step >= 16') Pour Richardson, la matrice d'itération dépend de <math><mrow><mi>&gamma;</mi></mrow></math>
      .align-center.bordered(v-if='step >= 17') Possibilité de choisir un <math><mrow><mi>&gamma;</mi></mrow></math> pour lequel la méthode converge
  .subslide(v-if='step > 17 && step <= 20')
    .eg-slide-content
      h2 Choix du paramètre <math><mrow><mi>&gamma;</mi></mrow></math>
      p Objectifs
      #objectifs
        .subgauche
          #g1(v-if='step >= 19') 1. Assurer la convergence
          #g2(v-if='step >= 20') 2. Minimiser le temps de convergence
        .subdroite
          #d1.align-center(v-if='step >= 19')
            <math>
              <mrow>
              <mi>&rho;</mi>
              <mrow>
              <mo form="prefix">(</mo>
              <mi>R</mi>
              <mo form="prefix">(</mo>
              <mi>&gamma;</mi>
              <mo form="postfix">)</mo>
              <mo form="postfix">)</mo>
              </mrow>
              <mo>=</mo>
              <mstyle displaystyle="true">
              <munder>
              <mi>max</mi>
              <mi>i</mi>
              </munder>
              </mstyle>
              <mrow>
              <mo form="prefix">(</mo>
              <mo>|</mo>
              <mn>1</mn>
              <mo>-</mo>
              <mi>&gamma;</mi>
              <msub>
              <mi>&lambda;</mi>
              <mi>i</mi>
              </msub>
              <mo>|</mo>
              <mo form="postfix">)</mo>
              </mrow>
              </mrow>
            </math>
          #2.align-center(v-if='step >= 20')
            <math>
              <mrow>
              <msub>
              <mi>&gamma;</mi>
              <mrow>
              <mi>o</mi>
              <mi>p</mi>
              <mi>t</mi>
              <mi>i</mi>
              <mi>m</mi>
              <mi>a</mi>
              <mi>l</mi>
              </mrow>
              </msub>
              <mo>=</mo>
              <mfrac linethickness="1">
              <mn>2</mn>
              <mrow>
              <msub>
              <mi>&lambda;</mi>
              <mn>1</mn>
              </msub>
              <mo>+</mo>
              <msub>
              <mi>&lambda;</mi>
              <mi>n</mi>
              </msub>
              </mrow>
              </mfrac>
              </mrow>
            </math>
</template>

<script>
import eagle from 'eagle.js'
export default {
  props: {
    steps: { default: 21 },
    nomdumec: { default: 'Inconnu' }
  },
  components: {
  },
  mixins: [eagle.slide]
}
</script>
<style lang='scss' scoped>
.eg-slide, .subslide {
  .eg-slide-content {
    display: grid;
    grid-row-gap: 10px;

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

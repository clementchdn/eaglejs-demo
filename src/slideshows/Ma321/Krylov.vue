<template lang="pug">
eg-transition(:enter='enter', v-if="step <=27")
  .eg-slide(v-if='active && step < 6')
    #krykry
      .subgauche
        p Les sous-espaces de Krylov, introduits en 1931 par le mathématicien éponyme, englobent un ensemble de méthodes permettant de résoudre différents problèmes de mathématiques.
        ul(v-if="step>=1")
          li(v-if="step>=2") Réolution de systèmes linéaires
          li(v-if="step>=3") Minimisation
          li(v-if="step>=4") Problèmes de valeurs propres
          li(v-if="step>=5") ...
      .subdroite
        img(src='./Ivan_Krylov.jpg' style='width: 400px;')
  eg-transition(leave='slideOutLeft' v-if="step === 6")
    .subslide
        h3 De Jacobi à Krylov :
        p On introduit les sous espaces de Krylov grâce à la méthode de Jacobi :
        .align-center
          <math>
            <mrow>
            <msup>
            <mi>x</mi>
            <mrow>
            <mi>k</mi>
            <mo>+</mo>
            <mn>1</mn>
            </mrow>
            </msup>
            <mo>=</mo>
            <mo>-</mo>
            <msup>
            <mi>D</mi>
            <mn>-1</mn>
            </msup>
            <mrow>
            <mo form="prefix">(</mo>
            <mi>L</mi>
            <mo>+</mo>
            <mi>U</mi>
            <mo form="postfix">)</mo>
            </mrow>
            <msup>
            <mi>x</mi>
            <mi>k</mi>
            </msup>
            <mo>+</mo>
            <msup>
            <mi>D</mi>
            <mn>-1</mn>
            </msup>
            <mi>b</mi>
            <mo>=</mo>
            <mrow>
            <mo form="prefix">(</mo>
            <mi>I</mi>
            <mo>-</mo>
            <msup>
            <mi>D</mi>
            <mn>-1</mn>
            </msup>
            <mi>A</mi>
            <mo form="postfix">)</mo>
            </mrow>
            <msup>
            <mi>x</mi>
            <mi>k</mi>
            </msup>
            <mo>+</mo>
            <msup>
            <mi>D</mi>
            <mn>-1</mn>
            </msup>
            <mi>b</mi>
            </mrow>
          </math>
        p Avec <math>
          <mrow>
          <mi>A</mi>
          <mo>=</mo>
          <mi>D</mi>
          <mo>+</mo>
          <mi>L</mi>
          <mo>+</mo>
          <mi>U</mi>
          </mrow></math>, <math>
          <mrow>
          <mi>L</mi>
          </mrow></math> une matrice triangulaire inférieure, <math><mrow><mi>U</mi></mrow></math> une matrice triangulaire supérieure et <math><mrow><mi>D</mi></mrow></math> diagonale.
        .align-center
          <math>
            <mrow>
            <msup>
            <mi>r</mi>
            <mi>k</mi>
            </msup>
            <mo>&#x0225C;</mo>
            <mi>b</mi>
            <mo>-</mo>
            <mi>A</mi>
            <msup>
            <mi>x</mi>
            <mi>k</mi>
            </msup>
            <mo>=</mo>
            <mo>-</mo>
            <mi>A</mi>
            <mrow>
            <mo form="prefix">(</mo>
            <mo>-</mo>
            <msup>
            <mi>A</mi>
            <mn>-1</mn>
            </msup>
            <mi>b</mi>
            <mo>+</mo>
            <msup>
            <mi>x</mi>
            <mi>k</mi>
            </msup>
            <mo form="postfix">)</mo>
            </mrow>
            <mo>=</mo>
            <mo>-</mo>
            <mi>A</mi>
            <mrow>
            <mo form="prefix">(</mo>
            <mo>-</mo>
            <msup>
            <mi>x</mi>
            <mo>*</mo>
            </msup>
            <mo>+</mo>
            <msup>
            <mi>x</mi>
            <mi>k</mi>
            </msup>
            <mo form="postfix">)</mo>
            </mrow>
            </mrow>
          </math>
        p Où <math>
          <mrow>
          <msup>
          <mi>x</mi>
          <mo>*</mo>
          </msup>
          </mrow></math> est la solution réelle du système. En normalisant le système ci-dessus de telle que <math><mrow><mi>D</mi><mi>=</mi><mi>I</mi></mrow></math>. Alors, nous pouvons écrire la solution au rang <math><mrow><mi>k+1</mi></mrow></math>, comme celle au rang <math><mrow><mi>k</mi></mrow></math> plus le résidu :
        .align-center
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <mtable>
            <mtr>
            <mtd rowspan="4">
            <mspace/>
            </mtd>
            <mtd columnalign="right">
            <msup>
            <mi>x</mi>
            <mrow>
            <mi>k</mi>
            <mo>+</mo>
            <mn>1</mn>
            </mrow>
            </msup>
            </mtd>
            <mtd columnalign="left">
            <mo>=</mo>
            <msup>
            <mi>x</mi>
            <mi>k</mi>
            </msup>
            <mo>+</mo>
            <msup>
            <mi>r</mi>
            <mi>k</mi>
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
            <mi>x</mi>
            <mrow>
            <mi>k</mi>
            <mo>+</mo>
            <mn>1</mn>
            </mrow>
            </msup>
            <mo>-</mo>
            <msup>
            <mi>x</mi>
            <mo>*</mo>
            </msup>
            </mtd>
            <mtd columnalign="left">
            <mo>=</mo>
            <msup>
            <mi>x</mi>
            <mi>k</mi>
            </msup>
            <mo>-</mo>
            <msup>
            <mi>x</mi>
            <mo>*</mo>
            </msup>
            <mo>+</mo>
            <msup>
            <mi>r</mi>
            <mi>k</mi>
            </msup>
            </mtd>
            <mtd columnalign="right">
            <mspace/>
            </mtd>
            </mtr>
            <mtr>
            <mtd columnalign="right">
            <mo>&hArr;</mo>
            <mo>-</mo>
            <mi>A</mi>
            <mrow>
            <mo form="prefix">(</mo>
            <msup>
            <mi>x</mi>
            <mrow>
            <mi>k</mi>
            <mo>+</mo>
            <mn>1</mn>
            </mrow>
            </msup>
            <mo>-</mo>
            <msup>
            <mi>x</mi>
            <mo>*</mo>
            </msup>
            <mo form="postfix">)</mo>
            </mrow>
            </mtd>
            <mtd columnalign="left">
            <mo>=</mo>
            <mo>-</mo>
            <mi>A</mi>
            <mrow>
            <mo form="prefix">(</mo>
            <msup>
            <mi>x</mi>
            <mi>k</mi>
            </msup>
            <mo>-</mo>
            <msup>
            <mi>x</mi>
            <mo>*</mo>
            </msup>
            <mo form="postfix">)</mo>
            </mrow>
            <mo>-</mo>
            <mi>A</mi>
            <msup>
            <mi>r</mi>
            <mi>k</mi>
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
            <mi>r</mi>
            <mrow>
            <mi>k</mi>
            <mo>+</mo>
            <mn>1</mn>
            </mrow>
            </msup>
            </mtd>
            <mtd columnalign="left">
            <mo>=</mo>
            <msup>
            <mi>r</mi>
            <mi>k</mi>
            </msup>
            <mo>-</mo>
            <mi>A</mi>
            <msup>
            <mi>r</mi>
            <mi>k</mi>
            </msup>
            </mtd>
            <mtd columnalign="right">
            <mspace/>
            </mtd>
            </mtr>
            </mtable>
          </math>
  eg-transition(enter='bounceInRight' v-if="step===7")
    .subslide
      p Nous reconnaissons une combinaison linéaire. En effet, <math>
          <mrow>
          <msup>
          <mi>r</mi>
          <mrow>
          <mi>k</mi>
          <mo>+</mo>
          <mn>1</mn>
          </mrow>
          </msup>
          </mrow></math> est une combinaison linéaire des <math>
          <mrow>
          <msup>
          <mi>A</mi>
          <mrow>
          <mi>k</mi>
          </mrow>
          </msup>
          <msup>
          <mi>r</mi>
          <mrow>
          <mn>0</mn>
          </mrow>
          </msup>
          </mrow></math> précédents. Cela mène à la construction du sous-espace de Krylov :
      .align-center
        <math xmlns="http://www.w3.org/1998/Math/MathML">
          <mrow>
          <msup>
          <mi>x</mi>
          <mi>k</mi>
          </msup>
          <mo>&isin;</mo>
          <msup>
          <mi>x</mi>
          <mn>0</mn>
          </msup>
          <mo>+</mo>
          <mi>V</mi>
          <mi>e</mi>
          <mi>c</mi>
          <mi>t</mi>
          <mrow>
          <mo form="prefix">{</mo>
          <msup>
          <mi>r</mi>
          <mn>0</mn>
          </msup>
          <mo>,</mo>
          <mi>A</mi>
          <msup>
          <mi>r</mi>
          <mn>0</mn>
          </msup>
          <mo>,</mo>
          <mo>.</mo>
          <mo>.</mo>
          <mo>.</mo>
          <mo>,</mo>
          <msup>
          <mi>A</mi>
          <mi>k</mi>
          </msup>
          <msup>
          <mi>r</mi>
          <mn>0</mn>
          </msup>
          <mo form="postfix">}</mo>
          </mrow>
          </mrow>
        </math>
      p Où <math>
          <mrow>
          <mi>V</mi>
          <mi>e</mi>
          <mi>c</mi>
          <mi>t</mi>
          <mrow>
          <mo form="prefix">{</mo>
          <msup>
          <mi>r</mi>
          <mn>0</mn>
          </msup>
          <mo>,</mo>
          <mi>A</mi>
          <msup>
          <mi>r</mi>
          <mn>0</mn>
          </msup>
          <mo>,</mo>
          <mo>.</mo>
          <mo>.</mo>
          <mo>.</mo>
          <mo>,</mo>
          <msup>
          <mi>A</mi>
          <mi>k</mi>
          </msup>
          <msup>
          <mi>r</mi>
          <mn>0</mn>
          </msup>
          <mo form="postfix">}</mo>
          </mrow>
          </mrow></math> est le k-ième espace de Krylov généré par <math><mi>A</mi></math> à partir de <math><msup><mrow><mi>r</mi></mrow><mn>0</mn></mrow></msup></math>, noté <math>
            <mrow>
            <msub>
            <mi>&Kscr;</mi>
            <mi>k</mi>
            </msub>
            <mrow>
            <mo form="prefix">(</mo>
            <mi>A</mi>
            <mo>,</mo>
            <msup>
            <mi>r</mi>
            <mn>0</mn>
            </msup>
            <mo form="postfix">)</mo>
            </mrow>
            </mrow></math>
  .eg-slide(enter='slideInRight' v-if="step >=8 && step <=20")
      p Les espaces de Krylov sont énormément utilisés pour plusieurs de leurs propriétés :
        ul
          li(v-if="step >=9") La solution de notre problème appartient à l'espace de Krylov de dimension <math><mi>n</mi></math> si l'on pose <math>
              <mrow>
              <msub>
              <mi>r</mi>
              <mn>0</mn>
              </msub>
              <mo>=</mo>
              <mi>b</mi>
              </mrow></math>
              toggle-button.inline.small-margin-left(v-model="demo1")
          li(v-if="step >=10") L'algorithme à base de sous-espaces de Krylov converge en <math><mi>n</mi></math> itérations maximales.
              toggle-button.inline.small-margin-left(v-model="demo2")
      eg-transition(enter='slideInRight', leave='zoomOut')
        #awesome-embedded.embedded-slideshow-container(v-if='(demo1 || demo2) && (step >= 11 && step <=20)')
          demoKrylov(:embedded='true', :mouseNavigation='false', :demo1='demo1', :demo2='demo2', :steps='10')
  .eg-slide(v-if="step >=21 && step < 27")
    ul(v-if='step >= 21')
      li Construire les sous-espaces K et L
      li Chercher la nouvelle itération dans <math><mi>u</mi><mo>+</mo><mi>K</mi></math> par le procédé exposé ci-dessus.
    p Voici donc le principe général des méthodes de projection :
    ul(v-if='step >= 22')
      li(v-if='step >= 22') Choisir <math><mrow><msup><mi>&Kopf;</mi><mi>m</mi></msup></mrow></math> et <math><mrow><msup><mi>&Lopf;</mi><mi>m</mi></msup></mrow></math> deux sous-espaces de <math><mrow><msup><mi>&Ropf;</mi><mi>n</mi></msup></mrow></math> de même dimension <math><mi>m</mi></math>
      li(v-if='step >= 23') Construire <math><msub><mrow><mi>V</mi></mrow><mi>m</mi></msub></math> et <math><msub><mrow><mi>W</mi></mrow><mi>m</mi></msub></math>
      li(v-if='step >= 24') Calculer le résidu <math><mrow><mi>r</mi><mo>=</mo><mi>b</mi><mo>-</mo><mi>A</mi><msup><mi>x</mi><mrow><mo form="prefix">(</mo><mi>k</mi><mo form="postfix">)</mo></mrow></msup></mrow></math>
      li(v-if='step >= 25') Résoudre le système <math><mrow><mi>y</mi><mo>=</mo><msup><mrow><mo form="prefix">(</mo><msubsup><mi>W</mi><mi>m</mi><mi>t</mi></msubsup><mi>A</mi><msub><mi>V</mi><mi>m</mi></msub><mo form="postfix">)</mo></mrow><mn>-1</mn></msup><msubsup><mi>W</mi><mi>m</mi><mi>t</mi></msubsup><mi>r</mi></mrow></math>
      li(v-if='step >= 26') Créer la nouvelle solution : <math><mrow><mi>x</mi><mo>=</mo><mi>x</mi><mo>+</mo><msub><mi>V</mi><mi>m</mi></msub><mi>y</mi></mrow></math>
  #codeGMRES(v-if="step === 27")
    .subgauche(v-if="step === 27")
      h3 Algorithme de GMRES
      img.center(src="./gmres.png")
    .subdroite(v-if="step === 27")
      h3 Code python utilisé
      img.center(src="./gmresPython.png")
</template>
<script>
import eagle from 'eagle.js'
export default {
  data: function () {
    return {
      demo1: false,
      demo2: false
    }
  },
  props: {
    steps: { default: 28 },
    nomdumec: { default: 'Inconnu' }
  },
  components: {
    demoKrylov: require('./DemoKrylov.vue').default
  },
  mixins: [eagle.slide]
}
</script>
<style lang='scss' scoped>
.eg-slide {
  height: 100%;
  .subslide{
    .align-center {
      text-align: center;
    }
  }
  .center {
    margin-left: auto;
    margin-right: auto;
  }
  #awesome-embedded {
    position: relative;
    margin: 0 auto;
    width: 80%;
    height: 66vh;
    background: white;
  }
}
#codeGMRES, #krykry {
  height: 100%;
  width: 100%;
  display: grid;
  grid-template-columns: 66% 34%;
  grid-column-gap: 1vw;
  .subgauche {
    display: grid;
    grid-template-rows: 5% 95%;
    height: 100%;
    margin: auto;
    grid-column: 1;
    p {grid-row: 1; margin-top: 10%}
    ul {grid-row: 2; margin-top : 25%;}
  }
  .subdroite {
    display: grid;
    grid-template-rows: 5% 95%;
    height: 100%;
    margin: auto;
    grid-column: 2;
    h3 {grid-row: 1;}
    img {grid-row: 2; margin-top: 20%}
  }
}
</style>

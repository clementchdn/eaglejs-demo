<template lang="pug">
#DemoKrylov
  .eg-slideshow(style="background-color: white; border: 1px solid black; padding: 10px")
    slide(enter='fadeIn', steps='5' v-if='demo1')
      .align-center
        <math><mrow><mi>Ax</mi><mo>=</mo><mi>b</mi></mrow></math>
      p D'après la définition du problème, la matrice <math><mi>A</mi></math> est inversible. Nous supposons que l'on a le polynôme caractéristique de <math><mi>A</mi></math> :
      eg-transition(enter='fadeIn')
        .align-center.smaller(v-if="step >= 2")
          <math>
          <mrow>
          <mi>P</mi>
          <mrow>
          <mo form="prefix">(</mo>
          <mi>&lambda;</mi>
          <mo form="postfix">)</mo>
          </mrow>
          <mo>=</mo>
          <mstyle displaystyle="true">
          <munderover>
          <mo>&sum;</mo>
          <mrow>
          <mi>j</mi>
          <mo>=</mo>
          <mn>0</mn>
          </mrow>
          <mi>n</mi>
          </munderover>
          </mstyle>
          <msub>
          <mi>&alpha;</mi>
          <mi>j</mi>
          </msub>
          <msup>
          <mi>t</mi>
          <mi>j</mi>
          </msup>
          <mo>&rArr;</mo>
          <mi>P</mi>
          <mrow>
          <mo form="prefix">(</mo>
          <mn>0</mn>
          <mo form="postfix">)</mo>
          </mrow>
          <mo>=</mo>
          <msub>
          <mi>&alpha;</mi>
          <mn>0</mn>
          </msub>
          <mo>=</mo>
          <mo>&dd;</mo>
          <mi>e</mi>
          <mi>t</mi>
          <mrow>
          <mo form="prefix">(</mo>
          <mi>A</mi>
          <mo form="postfix">)</mo>
          </mrow>
          <mo>&ne;</mo>
          <mn>0</mn>
          </mrow>
          </math>
      eg-transition(enter='fadeIn')
        p(v-if="step >=3") Par le théorème de Cayley-Hamilton, nous pouvons obtenir la valeur de <math><mrow><msup><mi>A</mi><mn>-1</mn></msup></mrow></math> :
      eg-transition(enter='slideInRight')
        .align-center.smaller.smaller(v-if="step >=4")
          <math>
            <mtable class="m-align-starred">
            <mtr>
            <mtd rowspan="4">
            <mspace/>
            </mtd>
            <mtd columnalign="right">
            <mi>P</mi>
            <mrow>
            <mo form="prefix">(</mo>
            <mi>A</mi>
            <mo form="postfix">)</mo>
            </mrow>
            <mo>=</mo>
            <msub>
            <mi>&alpha;</mi>
            <mn>0</mn>
            </msub>
            <mi>I</mi>
            <mo>+</mo>
            <msub>
            <mi>&alpha;</mi>
            <mn>1</mn>
            </msub>
            <mi>A</mi>
            <mo>+</mo>
            <mo>.</mo>
            <mo>.</mo>
            <mo>.</mo>
            <mo>+</mo>
            <msub>
            <mi>&alpha;</mi>
            <mi>n</mi>
            </msub>
            <msup>
            <mi>A</mi>
            <mi>n</mi>
            </msup>
            <mo>=</mo>
            <mn>0</mn>
            </mtd>
            <mtd columnalign="right">
            <mspace/>
            </mtd>
            </mtr>
            <mtr>
            <mtd columnalign="right">
            <msub>
            <mi>&alpha;</mi>
            <mn>0</mn>
            </msub>
            <msup>
            <mi>A</mi>
            <mn>-1</mn>
            </msup>
            <mi>A</mi>
            <mo>+</mo>
            <msub>
            <mi>&alpha;</mi>
            <mn>1</mn>
            </msub>
            <mi>A</mi>
            <mo>+</mo>
            <mo>.</mo>
            <mo>.</mo>
            <mo>.</mo>
            <mo>+</mo>
            <msub>
            <mi>&alpha;</mi>
            <mi>n</mi>
            </msub>
            <msup>
            <mi>A</mi>
            <mi>n</mi>
            </msup>
            <mo>=</mo>
            <mn>0</mn>
            </mtd>
            <mtd columnalign="right">
            <mspace/>
            </mtd>
            </mtr>
            <mtr>
            <mtd columnalign="right">
            <mrow>
            <mo rspace="0.3em" lspace="0em" stretchy="true" fence="true" form="prefix">(</mo>
            <msub>
            <mi>&alpha;</mi>
            <mn>0</mn>
            </msub>
            <msup>
            <mi>A</mi>
            <mn>-1</mn>
            </msup>
            <mo>+</mo>
            <msub>
            <mi>&alpha;</mi>
            <mn>1</mn>
            </msub>
            <mo>+</mo>
            <mo>.</mo>
            <mo>.</mo>
            <mo>.</mo>
            <mo>+</mo>
            <msub>
            <mi>&alpha;</mi>
            <mi>n</mi>
            </msub>
            <msup>
            <mi>A</mi>
            <mrow>
            <mi>n</mi>
            <mo>-</mo>
            <mn>1</mn>
            </mrow>
            </msup>
            <mo rspace="0em" lspace="0.3em" stretchy="true" fence="true" form="postfix">)</mo>
            </mrow>
            <mi>A</mi>
            <mo>=</mo>
            <mn>0</mn>
            </mtd>
            <mtd columnalign="right">
            <mspace/>
            </mtd>
            </mtr>
            <mtr>
            <mtd columnalign="right">
            <msub>
            <mi>&alpha;</mi>
            <mn>0</mn>
            </msub>
            <msup>
            <mi>A</mi>
            <mn>-1</mn>
            </msup>
            <mo>+</mo>
            <msub>
            <mi>&alpha;</mi>
            <mn>1</mn>
            </msub>
            <mo>+</mo>
            <mo>.</mo>
            <mo>.</mo>
            <mo>.</mo>
            <mo>+</mo>
            <msub>
            <mi>&alpha;</mi>
            <mi>n</mi>
            </msub>
            <msup>
            <mi>A</mi>
            <mrow>
            <mi>n</mi>
            <mo>-</mo>
            <mn>1</mn>
            </mrow>
            </msup>
            <mo>=</mo>
            <mn>0</mn>
            </mtd>
            <mtd columnalign="right">
            <mspace/>
            </mtd>
            </mtr>
            </mtable>
          </math>
      eg-transition(enter='slideInDown')
        .subslide(v-if="step >=5")
          p Ce qui donne finalement :
          .align-center.smaller.center
            <math>
              <mrow>
              <msup>
              <mi>A</mi>
              <mn>-1</mn>
              </msup>
              <mo>=</mo>
              <mo>-</mo>
              <mfrac linethickness="1">
              <mn>1</mn>
              <mrow>
              <msub>
              <mi>&alpha;</mi>
              <mn>0</mn>
              </msub>
              </mrow>
              </mfrac>
              <mo>&times;</mo>
              <mstyle displaystyle="true">
              <munderover>
              <mo>&sum;</mo>
              <mrow>
              <mi>j</mi>
              <mo>=</mo>
              <mn>0</mn>
              </mrow>
              <mrow>
              <mi>n</mi>
              <mo>-</mo>
              <mn>1</mn>
              </mrow>
              </munderover>
              </mstyle>
              <msub>
              <mi>&alpha;</mi>
              <mrow>
              <mi>j</mi>
              <mo>+</mo>
              <mn>1</mn>
              </mrow>
              </msub>
              <msup>
              <mi>A</mi>
              <mi>j</mi>
              </msup>
              </mrow>
            </math>
    slide(enter='lightSpeedIn' steps='5' v-if='demo2')
      p Dans cette partie, nous allons étudier un des algorithmes qui utilisent les principes précédents. Cet algorithme est l'algorithme GMRES. Il se base sur la projection des sous-espaces et la contion Petrov-Galerkin :
      .align-center(v-if="step >= 2")
        <math>
          <mrow>
          <mi>b</mi>
          <mo>-</mo>
          <mi>A</mi>
          <mi>x</mi>
          <mo>&perp;</mo>
          <mi>&Lopf;</mi>
          <mo>&rArr;</mo>
          <mo>&lt;</mo>
          <mi>A</mi>
          <mi>u</mi>
          <mo>,</mo>
          <mi>v</mi>
          <mo>&gt;</mo>
          <mo>=</mo>
          <mo>&lt;</mo>
          <mi>b</mi>
          <mo>,</mo>
          <mi>v</mi>
          <mo>&gt;</mo>
          <mo>,</mo>
          <mi>v</mi>
          <mo>&isin;</mo>
          <mi>&Lopf;</mi>
          </mrow>
        </math>
      p(v-if="step >= 3") Il nous faut maintenant trouver la solution de <math><mi>x</mi><mo>=</mo><msub><mrow><mi>x</mi></mrow><mn>0</mn></msub><mrow><mo>+</mo><mi>V</mi><mi>y</mi></mrow></math>. Alors, nous écrivons :
      .align-center(v-if="step >=4")
        <math>
          <mtable class="m-align-starred">
          <mtr>
          <mtd rowspan="4">
          <mspace/>
          </mtd>
          <mtd columnalign="right">
          <mo>&lt;</mo>
          <mi>A</mi>
          <mi>v</mi>
          <mo>,</mo>
          <mi>w</mi>
          <mo>&gt;</mo>
          </mtd>
          <mtd columnalign="left">
          <mo>=</mo>
          <mo>&lt;</mo>
          <mi>r</mi>
          <mn>0</mn>
          <mo>,</mo>
          <mi>w</mi>
          <mo>&gt;</mo>
          <mo>&forall;</mo>
          <mi>w</mi>
          <mo>&isin;</mo>
          <mi>L</mi>
          </mtd>
          <mtd columnalign="right" >
          <mspace/>
          </mtd>
          </mtr>
          <mtr>
          <mtd columnalign="right">
          <mo>&lt;</mo>
          <mi>A</mi>
          <mi>V</mi>
          <mi>y</mi>
          <mo>,</mo>
          <mi>W</mi>
          <mi>z</mi>
          <mo>&gt;</mo>
          </mtd>
          <mtd columnalign="left">
          <mo>=</mo>
          <mo>&lt;</mo>
          <mi>r</mi>
          <mn>0</mn>
          <mo>,</mo>
          <mi>W</mi>
          <mi>z</mi>
          <mo>&gt;</mo>
          <mo>&forall;</mo>
          <mi>z</mi>
          <mo>&isin;</mo>
          <msup>
          <mi>&Ropf;</mi>
          <mi>m</mi>
          </msup>
          </mtd>
          <mtd columnalign="right" >
          <mspace/>
          </mtd>
          </mtr>
          <mtr>
          <mtd columnalign="right">
          <mi>A</mi>
          <mi>v</mi>
          <mi>y</mi>
          </mtd>
          <mtd columnalign="left">
          <mo>=</mo>
          <mi>r</mi>
          <mn>0</mn>
          </mtd>
          <mtd columnalign="right" >
          <mspace/>
          </mtd>
          </mtr>
          <mtr>
          <mtd columnalign="right">
          <mi>y</mi>
          </mtd>
          <mtd columnalign="left">
          <mo>=</mo>
          <msup>
          <mrow>
          <mo form="prefix">(</mo>
          <msup>
          <mi>W</mi>
          <mi>t</mi>
          </msup>
          <mi>A</mi>
          <mi>V</mi>
          <mo form="postfix">)</mo>
          </mrow>
          <mn>-1</mn>
          </msup>
          <msup>
          <mi>W</mi>
          <mi>t</mi>
          </msup>
          <msup>
          <mi>r</mi>
          <mn>0</mn>
          </msup>
          </mtd>
          <mtd columnalign="right" >
          <mspace/>
          </mtd>
          </mtr>
          </mtable>
        </math>
      p(v-if="step >= 5") Nous obtenons donc la solution :
        .align-center(v-if="step >= 5")
          <math>
            <mrow>
            <mi>x</mi>
            <mo>=</mo>
            <msub>
            <mi>x</mi>
            <mn>0</mn>
            </msub>
            <mo>+</mo>
            <mi>V</mi>
            <msup>
            <mrow>
            <mo form="prefix">(</mo>
            <msup>
            <mi>W</mi>
            <mi>t</mi>
            </msup>
            <mi>A</mi>
            <mi>V</mi>
            <mo form="postfix">)</mo>
            </mrow>
            <mn>-1</mn>
            </msup>
            <msup>
            <mi>W</mi>
            <mi>t</mi>
            </msup>
            <msup>
            <mi>r</mi>
            <mn>0</mn>
            </msup>
            </mrow>
          </math>
</template>

<script>
import eagle from 'eagle.js'

export default {
  mixins: [eagle.slideshow],
  props: {
    demo1: { default: false },
    demo2: { default: false },
    steps: { default: 12 },
    preference: { default: 'baby bunnies' },
    username: { default: 'Tracy' }
  },
  data: function () {
    return {
      step: 1
    }
  },
  infos: {
    title: 'Deadpool',
    description: 'Demo embedded slideshow',
    path: 'deadpool'
  },
  components: {
  }
}
</script>

<style lang='scss'>
#DemoKrylov{
  .eg-slideshow {
    background-color: white !important;
    .eg-slide {
      .eg-slide-content, .subslide{
        h1, h2, h3, h4, p {
          font-weight: normal;
        }
        .smaller {
          math > * {
            font-size: 80%;
          }
        }
      }
    }
  }
}
</style>

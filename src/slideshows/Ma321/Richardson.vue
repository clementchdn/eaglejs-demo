<template lang="pug">
eg-transition(:nomdumec='nomdumec')
  .eg-slide(v-if='active')
    .eg-slide-content
      h3 Richardson
      p {{nomdumec}}
      #subgauche
        <math id="eq1">
          <mtable>
          <mtr>
          <mtd>
          <mspace/>
          </mtd>
          <mtd columnalign="left">
          <mi>P</mi>
          <mo>=</mo>
          <mi>&beta;</mi>
          <mi>I</mi>
          <mtable>
          <mtr>
          <mtd>
          <mtext>
          p.small-margin-left.small-margin-right avec
          <math xmlns="http://www.w3.org/1998/Math/MathML">
          <mrow>
          p.small-margin-left
          <mi> I </mi>
          </mrow>
          </math>
          p.small-margin-left.small-margin-right la matrice identité et
          <math xmlns="http://www.w3.org/1998/Math/MathML">
          <mrow>
          p.small-margin-left
          <mi>&beta;</mi>
          <mo>&isin;</mo>
          <msup>
          <mi>&Ropf;</mi>
          <mo>*</mo>
          </msup>
          </mrow>
          </math>
          </mtext>
          </mtd>
          </mtr>
          </mtable>
          </mtd>
          <mtd>
          <mspace/>
          </mtd>
          </mtr>
          </mtable>
        </math>
        p Notre système s'écrit alors de la manière suivante :
        <math id="eq2">
          <mtable class="m-align-starred">
          <mtr>
          <mtd rowspan="2">
          <mspace/>
          </mtd>
          <mtd columnalign="right">
          <mi>&beta;</mi>
          <mi>I</mi>
          <mi>x</mi>
          </mtd>
          <mtd columnalign="left">
          <mo>=</mo>
          </mtd>
          <mtd rowspan="2">
          <mspace/>
          </mtd>
          <mtd columnalign="right">
          <mrow>
          <mo form="prefix">(</mo>
          <mi>&beta;</mi>
          <mi>I</mi>
          <mo>-</mo>
          <mi>A</mi>
          <mo form="postfix">)</mo>
          </mrow>
          <mi>x</mi>
          <mo>+</mo>
          <mi>b</mi>
          </mtd>
          <mtd columnalign="right">
          <mspace/>
          </mtd>
          </mtr>
          <mtr>
          <mtd columnalign="right">
          <mi>x</mi>
          </mtd>
          <mtd columnalign="left">
          <mo>=</mo>
          </mtd>
          <mtd columnalign="right">
          <mrow>
          <mo form="prefix">(</mo>
          <mi>I</mi>
          <mo>-</mo>
          <mfrac linethickness="1.5px">
          <mn>1</mn>
          <mi>&beta;</mi>
          </mfrac>
          <mi>A</mi>
          <mo form="postfix">)</mo>
          </mrow>
          <mi>x</mi>
          <mo>+</mo>
          <mfrac linethickness="1.5px">
          <mn>1</mn>
          <mi>&beta;</mi>
          </mfrac>
          <mi>b</mi>
          </mtd>
          <mtd columnalign="right">
          <mspace/>
          </mtd>
          </mtr>
          </mtable>
        </math>
        p Pour simplifier, nous écrirons
        <math>
          <mrow>
          <mi>x</mi>
          <mo>=</mo>
          <mrow>
          <mo form="prefix">(</mo>
          <mi>I</mi>
          <mo>-</mo>
          <mi>&gamma;</mi>
          <mi>A</mi>
          <mo form="postfix">)</mo>
          </mrow>
          <mi>x</mi>
          <mo>+</mo>
          <mi>&gamma;</mi>
          <mi>b</mi>
          <mtable>
          <mtr>
          <mtd>
          <mtext>
          p.small-margin-left avec
          <math>
          <mrow>
          p.small-margin-left <mi>&gamma;</mi>
          <mo>=</mo>
          <mfrac linethickness="1.5px">
          <mn>1</mn>
          <mi>&beta;</mi>
          </mfrac>
          </mrow>
          </math>
          </mtext>
          </mtd>
          </mtr>
          </mtable>
          </mrow>
        </math>
      #subdroite.subslide
        <math xmlns="http://www.w3.org/1998/Math/MathML">
          <mrow>
          <mo rspace="0.3em" lspace="0em" stretchy="true" fence="true" form="prefix">{</mo>
          <mtable class="m-cases" columnalign="left">
          <mtr>
          <mtd>
          <mo>-</mo>
          <mn>3</mn>
          <mi>x</mi>
          <mo>+</mo>
          <mn>2</mn>
          <mi>y</mi>
          <mo>=</mo>
          <mn>1</mn>
          </mtd>
          </mtr>
          <mtr>
          <mtd>
          <mi>x</mi>
          <mo>+</mo>
          <mo>-</mo>
          <mn>4</mn>
          <mi>y</mi>
          <mo>=</mo>
          <mo>-</mo>
          <mn>7</mn>
          </mtd>
          </mtr>
          </mtable>
          <mphantom rspace="0em" lspace="0.3em" stretchy="true" fence="true" form="postfix">}</mphantom>
          </mrow>
        </math>
</template>

<script>
import eagle from 'eagle.js'
export default {
  props: {
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

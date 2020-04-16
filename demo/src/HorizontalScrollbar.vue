<template>
  <div>
    <scrolly class="horizontal-scrollbar-demo" @scrollchange="logScrollLayout">
      <scrolly-viewport>
        <article :style="{ width: width + '%' }">
          <button type="button" class="button" @click="addParagraph">Add Paragraph</button>
          <button type="button" class="button" @click="removeParagraph">Remove Paragraph</button>
          <button type="button" class="button" @click="extendWidth">Extend Width</button>
          <button type="button" class="button" @click="reduceWidth">Reduce Width</button>
          <bob-ross-lipsum :paragraphs="paragraphs"></bob-ross-lipsum>
        </article>
      </scrolly-viewport>
      <scrolly-bar axis="x axis-x_top"></scrolly-bar>
      <scrolly-bar axis="x axis-x_bottom"></scrolly-bar>
    </scrolly>
  </div>

</template>

<script>
import { Scrolly, ScrollyViewport, ScrollyBar } from '@/src';
import BobRossLipsum from './BobRossLipsum';

export default {
  mounted() {

  },

  data() {
    return {
      paragraphs: 4,
      width: 200,
      bLeft: 0,
      tLeft: 0
    }
  },

  components: {
    Scrolly,
    ScrollyViewport,
    ScrollyBar,
    BobRossLipsum
  },

  methods: {

    addParagraph() {
      this.paragraphs += 1;
    },

    removeParagraph() {
      this.paragraphs -= 1;
      if (this.paragraphs <= 1) {
        this.paragraphs = 1;
      }
    },

    extendWidth() {
      this.width += 50;
    },

    reduceWidth() {
      this.width -= 50;
      if (this.width <= 100) {
        this.width = 100;
      }
    },

    logScrollLayout(scrollLayout) {
      // console.log('scrollLayout:', scrollLayout);
      // this.bLeft = document.querySelector('.axis-x_top').style.left
      // this.tLeft = document.querySelector('.axis-x_bottom').style.left
    }
  }
};
</script>

<style lang="scss">
.horizontal-scrollbar-demo {
  width: 100%;
  height: 300px;
  border: 1px solid #ccc;

  article {
    padding: 15px;
  }

  p {
    margin-top: 10px;
  }
}
</style>

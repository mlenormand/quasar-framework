<template>
  <quasar-slider v-ref:slider arrows fullscreen class="text-white bg-black quasar-gallery-slider">
    <div
      v-for="img in src"
      track-by="$index"
      slot="slide"
      class="no-padding flex items-center justify-center"
    >
      <div>
        <img :src="img">
      </div>
    </div>

    <i slot="action" @click="toggleQuickView()">view_carousel</i>

    <div
      class="quasar-gallery-slider-quickview"
      :class="{active: quickView}"
    >
      <div v-for="img in src" track-by="$index">
        <img
          :src="img"
          :class="{active: $refs.slider.slide === $index}"
          @click="selectImage($index)"
        >
      </div>
    </div>
  </quasar-slider>
</template>

<script>
export default {
  props: {
    src: {
      type: Array,
      required: true
    }
  },
  data () {
    return {
      quickView: false
    }
  },
  methods: {
    toggleQuickView () {
      this.quickView = !this.quickView
    },
    selectImage (index) {
      this.$refs.slider.goToSlide(index, true)
      this.toggleQuickView()
    }
  }
}
</script>

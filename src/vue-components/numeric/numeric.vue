<template>
  <div class="quasar-numeric row inline items-center">
    <i @click="increment(-1)">remove</i>
    <input
      type="text"
      v-model="model"
      class="quasar-input-field"
      :style="{width: (''+model).length * 11 + 15 + 'px'}"
      :debounce="debounce"
      lazy
      number
    >
    <i @click="increment(1)">add</i>
  </div>
</template>

<script>
export default {
  props: {
    model: {
      type: Number,
      default: 0,
      coerce: (value) => parseFloat(value, 10) || 0
    },
    step: {
      type: Number,
      default: 1,
      coerce: (value) => parseFloat(value, 10)
    },
    debounce: Number,
    min: Number,
    max: Number
  },
  watch: {
    model (value) {
      if (typeof this.min === 'number' && value < this.min) {
        this.model = this.min
      }
      else if (typeof this.max === 'number' && value > this.max) {
        this.model = this.max
      }
    }
  },
  methods: {
    increment (direction) {
      this.model += direction * this.step
    }
  }
}
</script>

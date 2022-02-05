<script setup>
import BlurhashCanvas from './BlurhashCanvas.vue'
import { ref } from 'vue'
const props = defineProps({
  hash: {
      type: String,
      required: true
  },
  height: { 
    type: String,
    default: 'auto'
  },
  width: { 
    type: String,
    default: 'auto'
  },
  punch: { 
    type: Number,
    default: 1
  },
  resolutionY: {
      type: Number,
      default: 32
  },
  resolutionX: {
      type: Number,
      default: 32
  },
  src: {
    type: String,
    requried: true,
  }
})

const emit = defineEmits(['imageLoaded'])

let visible = ref(false)

let hideBlurhashOnImageLoad = () => {
  visible.value = true
  emit('imageLoaded')
}
</script>
<template>
<div>
    <blurhash-canvas :hash="hash" :punch="punch" :height="resolutionY" :width="resolutionX" class="canvasStyle"></blurhash-canvas>
    <img :src="src" class="canvasStyle" :onload="hideBlurhashOnImageLoad">
</div>
</template>
<style scoped>
.canvasStyle {
    position: absolute;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    width: 100%;
    height: 100%;
}
div {
    display: inline-block;
    position: relative;
    width: v-bind(width);
    height: v-bind(height);
}
</style>

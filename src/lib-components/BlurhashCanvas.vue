<script setup>
import { onMounted, onUpdated, ref } from 'vue'
import { decode } from 'blurhash';

const props = defineProps({
  hash: {
      type: String,
      required: true
  },
  height: { 
    type: Number,
    default: 128
  },
  width: { 
    type: Number,
    default: 128
  },
  punch: { 
    type: Number,
    default: 1
  }
})

const canvas = ref(null)

let draw = () => {
  const { hash, height, punch, width } = props;
  if (canvas.value) {
    const pixels = decode(hash, width, height, punch);

    const ctx = canvas.value.getContext('2d');
    const imageData = ctx.createImageData(width, height);
    imageData.data.set(pixels);
    ctx.putImageData(imageData, 0, 0);
  }
}

onMounted(() => {
  draw();
})

onUpdated(() => {
  draw();
})
</script>

<template>
  <canvas :height="height" :width="width" ref="canvas"/>
</template>
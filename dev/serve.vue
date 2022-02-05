<script>
import { defineComponent } from 'vue';
// Uncomment import and local "components" registration if library is not registered globally.
import { Vue3Blurhash } from '@/entry.esm';

export default defineComponent({
  name: 'ServeDev',
  // components: {
  //  Vue3BlurhashSample,
  // }
});
</script>

<template>
  <div id="app" style="height: 500px; width: 500px;">
    <vue3-blurhash src="https://blurha.sh/assets/images/img2.jpg" :punch="1" hash="LGF5]+Yk^6#M@-5c,1J5@[or[Q6." height="100%" width="100%" :resolutionX="10" :resolutionY="10"></vue3-blurhash>
  </div>
</template>

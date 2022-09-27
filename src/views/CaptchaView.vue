<script setup lang="ts">
  import FunnyCaptcha from '@/components/FunnyCaptcha.vue'
  import { ref } from 'vue'

  const showCaptcha = ref(true)
  const isCaptchaCorrect = ref(false)

  const processCaptcha = function(result : boolean) {
    // console.log(`Captcha = ${result}`);
    isCaptchaCorrect.value = result;
    showCaptcha.value = false;
  }

</script>

<template>
  <div>
    <h1>Captcha View</h1>
    <FunnyCaptcha
        v-if="showCaptcha"
        @correct="processCaptcha(true)"
        @incorrect="processCaptcha(false)"
        seconds="10"
    />

    <template v-else>
      <p v-if="isCaptchaCorrect">Oooofff at least you are sentient</p>
      <p v-else>Oh sorry, no place for robots here !</p>
    </template>
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>

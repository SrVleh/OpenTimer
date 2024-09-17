<script setup>
  import { ref, onMounted } from "vue";

  const props = defineProps({
    sessionsList: Array
  })

  let minutes = ref(0);
  let seconds = ref(0);

  function delay(ms) {
    return new Promise(resolve => setTimeout(resolve, ms));
  }

  async function startTimer() {
    for (let session of props.sessionsList) {
      let timer = session.for * 60; // Convert minutes to seconds

      while (timer >= 0) {
        let currentMinutes = parseInt(timer / 60, 10);
        let currentSeconds = parseInt(timer % 60, 10);

        minutes.value = currentMinutes < 10 ? "0" + currentMinutes : currentMinutes;
        seconds.value = currentSeconds < 10 ? "0" + currentSeconds : currentSeconds;

        await delay(1000);

        timer--;
      }
      console.log(`${session.type} timer finished.`);
    }
  }

  onMounted(() => {
    if (props.sessionsList && props.sessionsList.length > 0) {
      startTimer();
    }
  });
</script>

<template>
  <h1>{{ minutes }} : {{ seconds }}</h1>
</template>

<style scoped>
</style>
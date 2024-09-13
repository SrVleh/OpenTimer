<script setup>
  import { ref, reactive } from "vue";

  const trainingTypes = reactive({
    AMRAP: "AMRAP",
    FT: "For Time",
    EMOM: "EMOM",
    TBT: "Tabata"
  })

  let sessionData = reactive({
    type: "",
    minutes: 1,
    loops: 0
  })
</script>

<template>
  <h1>Timer</h1>
  <p v-if="sessionData">{{ sessionData }}</p>
  <p>{{ sessionData.type }}</p>
  <p>{{ sessionData.minutes }}</p>
  <p>{{ sessionData.loops }}</p>
  <form>
    <fieldset>
      <label for="types">Choose training type:</label>
      <select name="types" id="types" v-model="sessionData.type">
        <option :value="trainingTypes.AMRAP">{{ trainingTypes.AMRAP }}</option>
        <option :value="trainingTypes.FT">{{ trainingTypes.FT }}</option>
        <option :value="trainingTypes.EMOM">{{ trainingTypes.EMOM }}</option>
        <option :value="trainingTypes.TBT">{{ trainingTypes.TBT }}</option>
      </select>
    </fieldset>

    <fieldset>
      <label for="minutes">Minutes</label>
      <input type="number" min="1" value="1" v-model="sessionData.minutes" id="minutes" placeholder="1">
    </fieldset>

    <fieldset v-if="sessionData.type == trainingTypes.EMOM">
      <label for="loops">Loops</label>
      <input type="number" min="1" id="loops" v-model="sessionData.loops">
    </fieldset>
  </form>
</template>

<style scoped>

</style>
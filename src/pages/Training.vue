<script setup>
  import { ref, reactive } from "vue";

  const trainingTypes = reactive({
    AMRAP: "AMRAP",
    FT: "For Time",
    EMOM: "EMOM",
    TBT: "Tabata",
    RST: "Rest"
  })
  let newSessionData = reactive({
    type: "",
    for: 1,
    every: 1
  })
  let isNewSession = ref(false);
  let sessionsList = reactive([])

  function addSessionToList() {
    let sessionData = { ...newSessionData }
    sessionsList.push(sessionData)
    resetFormData()
  }

  function resetFormData() {
    newSessionData.type = "";
    newSessionData.for = 1;
    newSessionData.every = 1;
  }

</script>

<template>
  <h1>Timer</h1>

  <div v-for="session in sessionsList" style="width: 100%; border: 1px solid white; border-radius: 8px; display:flex; flex-direction: column; justify-content: center; align-items: center;">
    <h3>{{ session.type }}</h3>
    <p v-if="session.type === trainingTypes.EMOM">Every: {{ session.every }} minutes</p>
    <p>For: {{ session.for }} minutes</p>
  </div>

  <form>
    <button type="button" v-on:click="isNewSession = !isNewSession" v-if="!isNewSession">Add new training</button>

    <fieldset v-if="isNewSession">
      <fieldset>
        <label for="types">Choose training type:</label>
        <select name="types" id="types" v-model="newSessionData.type">
          <option :value="trainingTypes.AMRAP">{{ trainingTypes.AMRAP }}</option>
          <option :value="trainingTypes.FT">{{ trainingTypes.FT }}</option>
          <option :value="trainingTypes.EMOM">{{ trainingTypes.EMOM }}</option>
          <option :value="trainingTypes.TBT">{{ trainingTypes.TBT }}</option>
          <option :value="trainingTypes.RST">{{ trainingTypes.RST }}</option>
        </select>
      </fieldset>

      <fieldset>
        <label for="minutes">During minutes:</label>
        <input type="number" min="1" value="1" v-model="newSessionData.for" id="minutes" placeholder="1">
      </fieldset>

      <fieldset v-if="newSessionData.type === trainingTypes.EMOM">
        <label for="loops">Every minutes</label>
        <input type="number" min="1" id="loops" v-model="newSessionData.every">
      </fieldset>
    </fieldset>

    <button type="button" v-if="isNewSession" v-on:click="addSessionToList">Add to session</button>
    <button type="button">Start training!</button>
  </form>
</template>

<style scoped>

</style>
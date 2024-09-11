<script setup>
import Card from "../shared/ui/Card.vue";
</script>

<template>
  <section class="cards-container">
    <Card link="#/" image="https://cdn-icons-png.flaticon.com/512/763/763965.png" card-title="Home"/>
    <Card link="#/about" image="https://cdn-icons-png.flaticon.com/512/763/763965.png" card-title="About"/>
    <Card link="#/non-existent-path" image="https://cdn-icons-png.flaticon.com/512/763/763965.png" card-title="Broken Link"/>
  </section>
</template>

<style scoped>
.cards-container {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 3rem;
}
</style>
<script setup>
  defineProps({
    link: String,
    image: String,
    cardTitle: String
  })
</script>

<template>
  <a :href="link" class="category-card">
    <img :src="image" alt="" class="category-card-image">
    <h2>{{ cardTitle }}</h2>
  </a>
</template>

<style scoped>
.category-card {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 1rem;
  width: 18rem;
  height: 18rem;
  border-radius: .75rem;
  padding: 1rem;
  background-color: #222327;
  cursor: pointer;
  transition: all .2s;
}

.category-card:hover {
  transform: scale(1.04);
}

.category-card-image {
  width: 8rem;
  height: 8rem;
}

@media only screen and (max-width: 810px) {
  .category-card {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 1rem;
    width: 18rem;
    height: 18rem;
    border-radius: .75rem;
    padding: 1rem;
    background-color: red;
    cursor: pointer;
    transition: all .2s;
  }
}

</style>
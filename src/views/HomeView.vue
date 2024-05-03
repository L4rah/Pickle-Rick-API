<template>
  <div class="character-container">
    <div v-for="character in characters" :key="character.id" class="character-card">
      <img :src="character.image" :alt="character.name" class="character-image">
      <div class="character-info">
        <p class="character-name">Name: {{ character.name }}</p>
        <p>Gender: {{ character.gender }}</p>
        <p>Species: {{ character.species }}</p>
        <p>Episodes: {{ character.episode.length }}</p>
        <p>Status: {{ character.status }}</p>
        <p>Current Location: {{ character.location.name }}</p>
      </div>
    </div>
  </div>
</template>

<script setup>
import { onMounted, reactive, ref } from 'vue';

let characters = reactive(ref([]));

onMounted(async () => {
  let url = "https://rickandmortyapi.com/api/character";
  try {
    while (url) {
      const response = await fetch(url);
      const data = await response.json();
      characters.value = [...characters.value, ...data.results];
      url = data.info.next;
    }
  } catch (error) {
    console.error(error);
  }
});
</script>

<style src="./ListCharactersStyles.css" scoped></style>

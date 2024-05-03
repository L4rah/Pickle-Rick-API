<template>
  <div class="character-container">
    <div v-for="character in characters" :key="character.id" class="character-card">
      <img :src="character.image" :alt="character.name" class="character-image">
      <div class="character-info">
        <p class="character-name">Name: {{ character.name }}</p>
        <p class="character-gender">Gender: {{ character.gender }}</p>
        <p class="character-species">Species: {{ character.species }}</p>
        <p class="character-episodes">Episodes: {{ character.episode.length }}</p>
        <p class="character-status">Status: {{ character.status }}</p>
        <p class="character-location">Current Location: {{ character.location.name }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      characters: []
    }
  },
  mounted() {
    fetch('https://rickandmortyapi.com/api/character')
     .then(response => response.json())
     .then(data => {
        this.characters = data.results;
      })
     .catch(error => console.error(error));
  }
}
</script>

<style src="./styles.css" scoped></style>

<template lang="html">
  <div>
    <!-- <h2>Film details</h2> -->
      <h2>{{ film.title }}</h2>
      <p>Director: {{ film.director }}</p>
      <p>Producer: {{ film.producer }}</p>
      <p>Release date: {{ film.release_date }}</p>
      <article>{{ film.description }}</article>
    <button v-on:click="handleClick">Add to my favourite Ghibli!</button>
    <button v-on:click="handleRemoveClick">Remove from my favourite Ghibli</button>
  </div>
</template>

<script>
import {eventBus} from '@/main.js';

export default {
  name: "film-details",
  props:['film'],
  methods: {
    handleClick(){
      eventBus.$emit('add-to-favs', this.film);
    },
    handleRemoveClick(){
      eventBus.$emit('remove-from-favs', this.film);
    }
  }
}
</script>

<style lang="css" scoped>
div {
  flex-basis: 35%;
  /* margin-right: 600px; */
  /* background-color: white; */
}

h2 {
  color: purple;
}
p {
  font-style: italic;
}

button {
    text-align: center;
    width: 75%;
    border-radius: 20px;
    background-color: #436AA3;
    color: white;
    font-family: Ghibli;
    font-size: 20px;
    padding: 20px;
    /* margin-right: 30px; */
    margin-top: 30px;
    cursor: pointer;
}
</style>

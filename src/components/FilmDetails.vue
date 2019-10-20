<template lang="html">
  <div>
    <h2>Film details</h2>
      <h3>{{ film.title }}</h3>
      <p>{{ film.description }}</p>
      <p>{{ film.director }}</p>
      <p>{{ film.producer }}</p>
      <p>{{ film.release_date }}</p>
    <button v-on:click="handleClick">Add to my favourite films</button>
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
    }
  }
}
</script>

<style lang="css" scoped>
div {
  flex-basis: 30%;
}
</style>

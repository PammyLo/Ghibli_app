<template lang="html">
  <div>
    <h1>Ghibli World</h1>
    <film-list :films="films"></film-list>
    <film-details v-if="selectedFilm" :film="selectedFilm"></film-details>
  </div>
</template>

<script>
import FilmList from '@/components/FilmList.vue';
import FilmDetails from '@/components/FilmDetails.vue';
import {eventBus} from '@/main.js'

export default {
  name: "app",
  data() {
    return {
      films: [],
      selectedFilm: null,
      favouriteFilms: []
    }
  },
  mounted() {
    fetch('https://ghibliapi.herokuapp.com/films')
    .then(result => result.json())
    .then(data => this.films = data);

    eventBus.$on('film-selected', (film) => {
      this.selectedFilm = film;
    });
  },
  components: {
    'film-list': FilmList,
    'film-details': FilmDetails
  }
}
</script>

<style lang="css" scoped>
</style>

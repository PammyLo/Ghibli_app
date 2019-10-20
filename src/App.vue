<template lang="html">
  <div>
    <h1>Ghibli World</h1>
    <film-list></film-list>
  </div>
</template>

<script>
import FilmList from '@/components/FilmList.vue';


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
    .then(data => this.films = data)
  },
  components: {
    'film-list': FilmList
  }
}
</script>

<style lang="css" scoped>
</style>

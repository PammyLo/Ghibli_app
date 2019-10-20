<template lang="html">
  <div>
    <h1>Studio Ghibli</h1>
    <film-search></film-search>
      <div class="main-container">
        <film-list :films="films"></film-list>
        <fav-film-list v-if='favouriteFilms.length' :favourites='favouriteFilms'>></fav-film-list>
        <film-details v-if="selectedFilm" :film="selectedFilm"></film-details>
      </div>
  </div>
</template>

<script>
import FilmList from '@/components/FilmList.vue';
import FilmDetails from '@/components/FilmDetails.vue';
import FavFilmList from '@/components/FavFilmList.vue';
import FilmSearch from '@/components/FilmSearch';
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
    eventBus.$on('add-to-favs', (film) => {
      if (!this.favouriteFilms.includes(film))
      {this.favouriteFilms.push(film)};
    });
    eventBus.$on('remove-from-favs', (filmToRemove) => {
      this.favouriteFilms = this.favouriteFilms
      .filter(film => film.title !== filmToRemove.title);
    });
    eventBus.$on('film-search', (filmToFind) => {
      this.selectedFilm = this.films
      .find(film => film.title.toLowerCase().includes(filmToFind.toLowerCase()));
    });
  },
  components: {
    'film-list': FilmList,
    'film-details': FilmDetails,
    'fav-film-list': FavFilmList,
    'film-search': FilmSearch
  }
}
</script>

<style lang="css">
body {
background-image: url(./assets/ghibli_minimal.png);
background-size: cover;
background-repeat: no-repeat;
background-image: x-transform (-1);
padding-left: 50px;
padding-top: 50px;
font-family: Ghibli;
font-size: 22px;
}
</style>

<style lang="css" scoped>

h1 {
  color: white;
  font-family: Ghibli Bold;
  font-size: 56px;
  text-align: center;
}

.main-container {
    display: flex;
    justify-content: flex-start;
  }

</style>

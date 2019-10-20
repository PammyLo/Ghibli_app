<template lang="html">
  <div>
    <h1>Studio Ghibli</h1>
      <div class="main-container">
        <film-list :films="films"></film-list>
        <film-details v-if="selectedFilm" :film="selectedFilm"></film-details>
      <!-- </div>
      <div class="fav-list"> -->
        <fav-film-list v-if='favouriteFilms.length' :favourites='favouriteFilms'>></fav-film-list>
      </div>
  </div>
</template>

<script>
import FilmList from '@/components/FilmList.vue';
import FilmDetails from '@/components/FilmDetails.vue';
import FavFilmList from '@/components/FavFilmList.vue';
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
  },
  components: {
    'film-list': FilmList,
    'film-details': FilmDetails,
    'fav-film-list': FavFilmList,
  }
}
</script>

<style lang="css">
body {
background-image: url(./assets/Ghibli_castle_in_sky_rotated.jpg);
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
  color: #436AA3;
  font-family: Ghibli Bold;
  font-size: 56px;
  text-align: center;
}
.main-container {
  /* width: 60%; */
    display: flex;
    justify-content: flex-start;
  }
/* .fav-list {
  width: 40%;
  display: flex;
} */
</style>

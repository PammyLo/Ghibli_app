<template lang="html">
  <div>
    <h2>All Ghibli Films</h2>
    <ul>
      <film-list-item v-for="(film, index) in films" :key="index" :film="film">
        {{ film.title }}
      </film-list-item>
    </ul>
  </div>

</template>

<script>
import FilmListItem from '@/components/FilmListItem.vue';

export default {
  name: "film-list",
  props: ['films'],
  components: {
    'film-list-item': FilmListItem
  }
}
</script>

<style lang="css" scoped>
div {
  flex-basis: 25%;
}
</style>

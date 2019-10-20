<template lang="html">
  <div>
    <ul>
      <li v-for="(film, index) in films" film="film"> {{ film.title }} </li>
    </ul>
  </div>

</template>

<script>
import FilmDetails from '@/components/FilmDetails.vue';

export default {
  name: "film-list",
  props: ['films'],
  components: {
    'film-details': FilmDetails
  }
}
</script>

<style lang="css" scoped>
</style>

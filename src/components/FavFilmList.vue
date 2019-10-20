<template lang="html">
<div>
  <h2>My Favourite Ghibli Films</h2>
  <ul>
    <fav-list-item v-for="(favourite, index) in favourites" :key="index" :film="favourite">
    </fav-list-item>
  </ul>
</div>
</template>

<script>
import FavListItem from '@/components/FavListItem.vue';

export default {
  name: "fav-film-list",
  props: ['favourites'],
  components: {
    'fav-list-item': FavListItem
  }
}
</script>

<style lang="css" scoped>
div {
  flex-basis: 30%;
}
</style>

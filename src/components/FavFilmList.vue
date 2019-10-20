<template lang="html">
<div>
  <h2>My Favourite Ghibli Films</h2>
  <ul>
    <li v-for="(film, index) in favourites" :key="index"> {{ film.title }}
    </li>
  </ul>
</div>
</template>

<script>
export default {
  name: "fav-film-list",
  props: ['favourites']
}
</script>

<style lang="css" scoped>
div {
  flex-basis: 30%;
}
</style>

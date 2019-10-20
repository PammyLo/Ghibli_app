<template lang="html">
<div class="main-container">
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
.main-container {
    display: flex;
    justify-content: space-between;
  }
</style>

<template lang="html">
  <div>
    <h2>Film details</h2>
    <h3>{{ film.title }}</h3>
    <p>{{ film.description }}</p>
    <p>{{ film.director }}</p>
    <p>{{ film.producer }}</p>
    <p>{{ film.release_date }}</p>
  </div>
</template>

<script>
export default {
  name: "film-details",
  props:['film'],
}
</script>

<style lang="css" scoped>
</style>

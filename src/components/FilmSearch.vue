<template lang="html">
  <div>
    Search: <input type="text" v-model="searchInput" v-on:keyup="handleSearchInput">
  </div>
</template>

<script>
import {eventBus} from '@/main.js';

export default {
  name: "film-search",
  data() {
    return {
      searchInput: null
    };
  },
  mounted() {
    this.handleSearchInput();
  },
  methods: {
    handleSearchInput() {
      eventBus.$emit('film-search', this.searchInput);
    }
  }
}
</script>

<style lang="css" scoped>
input {
  font-size: 20px;
  font-family: Ghibli;
  padding: 5px;
  border-radius: 10px;
  width: 200px;
}
</style>

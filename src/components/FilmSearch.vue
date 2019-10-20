<template lang="html">
  <input type="text" v-model="searchInput" v-on:keyup="handleSearchInput">
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
</style>

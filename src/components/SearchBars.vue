<script setup>
import SearchBar from './SearchBar.vue';
</script>

<template>
  <div class="searchbars-wrapper">
    <SearchBar form-action="https://duckduckgo.com/" placeholder="DuckDuckGo" />
    <SearchBar form-action="https://google.com/search" placeholder="Google" />
  </div>
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.searchbars-wrapper {
  width: 100%;
  min-width: 300px;
  flex-grow: 8;
  margin-left: auto;
}

</style>

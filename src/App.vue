<script setup>
import SearchBars from './components/SearchBars.vue'
import TheWelcome from './components/TheWelcome.vue'
import Clock from './components/Clock.vue';
import NotesList from './components/NotesList.vue'
</script>

<template>
  <header>
    <div class="line-wrapper">
      <Clock />
      <SearchBars />
    </div>
  </header>

  <main class="line-wrapper">
    <NotesList />
  </main>
</template>

<style>
@import './assets/base.css';

#app {
  max-width: 1440px;
  margin: 0 auto;
  padding: 2rem;

  font-weight: normal;
}

header {
  line-height: 1.5;
}

.line-wrapper {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: stretch;
}

@media (max-width: 800px) {
  .line-wrapper {
    flex-direction: column;
  }
}

a,
.green {
  text-decoration: none;
  color: hsla(160, 100%, 37%, 1);
  transition: 0.4s;
}

@media (hover: hover) {
  a:hover {
    background-color: hsla(160, 100%, 37%, 0.2);
  }
}

</style>

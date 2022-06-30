<script setup>
import { reactive, onMounted } from 'vue';
import SearchBar from './SearchBar.vue';

const localStorage = window.localStorage
const state = reactive({
  quote: 'Keep your head cool.'
})

const searchEngines = [
  {
    id: 1,
    name: 'DuckDuckGo',
    base: 'https://duckduckgo.com/'
  },
  {
    id: 2,
    name: 'Google',
    base: 'https://google.com/search'
  }
]

function changeQuote () {
  const newQuote = prompt('Дай мне новую мотивирующую цитатку')
  if (!newQuote) return
  state.quote = newQuote
  localStorage.setItem('quote', newQuote)
}

onMounted(() => {
  const existingQuote = localStorage.getItem('quote')
  if ( existingQuote ) {
    state.quote = existingQuote
  }
})
</script>

<template>
  <div class="searchbars-wrapper">
    <SearchBar
      v-for="engine in searchEngines"
      :form-action="engine.base"
      :placeholder="name"
    />
    <div class="quote" @click="changeQuote">
      {{ state.quote }}
    </div>
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

.quote {
  font-weight: bold;
  text-align: center;
  cursor: pointer;
}
</style>

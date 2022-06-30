<script setup>
import { reactive, onMounted } from "vue";
import SingleNote from "./SingleNote.vue";

const localStorage = window.localStorage

const state = reactive({
  items: [
    {
      id: 1,
      checked: false,
      value: 'Test test lorem ipsum'
    },
    {
      id: 2,
      checked: true,
      value: 'Lorem ipsum dolor sit amet why the hell should i manually type that'
    },
    {
      id: 3,
      checked: true,
      value: 'Don\'t forget to milk the cow!'
    }
  ]
})

function toggleCheck (item) {
  item.checked = !item.checked
  saveNotes()
}

function saveNotes () {
  const itemsAsString = JSON.stringify(state.items)
  localStorage.setItem('notes', itemsAsString)
}

onMounted(async () => {
  const savedNotes = localStorage.getItem('notes')
  if (!savedNotes) return
  state.items = await JSON.parse(savedNotes)
})
</script>

<template>
  <div class="notes-wrapper">
    <h3>Мои заметки</h3>
    <SingleNote
      v-for="item in state.items"
      :id="item.id"
      :checked="item.checked"
      :value="item.value"
      @toggleChecked="toggleCheck(item)"
    />
    <button value="+T"></button>
    <button value="+#"></button>
  </div>
</template>

<style scoped>
h3 {
  left: 10px;
  font-size: smaller;
  font-style: italic;
  text-transform: uppercase;
}

.notes-wrapper {
  flex-grow: 2;
  border-style: dashed;
  border-width: 1px;
  border-color: #94949e;
  border-radius: 10px;
  padding: 10px;
  margin-top: 20px;
}
</style>

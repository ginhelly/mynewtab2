<script setup>
import { reactive } from 'vue';

const props = defineProps({
  checked: {
    type: Boolean,
    default: false
  },
  value: String,
  id: Number
})
</script>

<template>
  <div class="note-wrapper">
    <div>
      <div class="note-content">
        <input
          type="checkbox"
          :id="'checkbox' + props.id"
          v-model="props.checked"
          @click="$emit('toggleChecked')"  
        />
        <span :class="{ 'note-content-checked': props.checked }">{{ props.value }}</span>
      </div>
    </div>
    <div style="min-width: 50px">
      <button value="FFFF" style="">E</button>
      <button value="FFFF" style="">D</button>
    </div>
  </div>
</template>

<style scoped>
.note-wrapper {
  display: flex;
  justify-content: space-between;
  align-items: stretch;
  margin-top: 8px;
}

input[type=checkbox] {
  margin-right: 5px;
  display: inline;
  width: 20px;
}

.note-content {
  display: inline-block;
  line-height: 1;
  text-align: left;
}

.note-content-checked {
  text-decoration: line-through;
}
</style>

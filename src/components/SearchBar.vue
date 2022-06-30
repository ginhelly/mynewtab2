<script setup>
defineProps({
  formAction: String,
  placeholder: String,
  searchKey: {
    type: String,
    default: 'q'
  }
})
</script>

<template>
  <form :action="formAction" :placeholder='placeholder'>
    <input
      type="search"
      :name="searchKey"
      style="background-image: url(https://www.fillmurray.com/45/45)"
      autocomplete="off"
    >
    <input style='display: none;' type="submit" :value="placeholder">
  </form>
</template>

<style scoped>
input[type=search] {
  width: 70%;
  box-sizing: border-box;
  border-style: solid;
  border-width: thin;
  border-color: #5f5f63;
  border-radius: 4px;
  font-size: 16px;
  background-color: #38383d;
  color: #dededf;
  background-position: 5px 5px; 
  background-repeat: no-repeat;
  padding: 12px 20px 12px 50px;
  height: 40px;
  margin: 5px auto
}

@media (max-width: 800px) {
  input[type=search] {
    width: 100%;
  }
}
</style>

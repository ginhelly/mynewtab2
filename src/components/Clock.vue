<script setup>
import { reactive, onMounted } from 'vue'

const state = reactive({
  time: '00-00',
  date: '01.01.1990',
  weekday: 'Понедельник'
})

const formatterDate = new Intl.DateTimeFormat("ru")
const formatterWeekday = new Intl.DateTimeFormat("ru", {
    weekday: 'long'
})

function updateTime () {
  const date = new Date()
  const hours = date.getHours()
  const minutes = checkSingleDigit(date.getMinutes())
  state.time = hours + ':' + minutes
  state.date = formatterDate.format(date)
  state.weekday = formatterWeekday.format(date)
}

function checkSingleDigit (digit) {
  return ('0' + digit).slice(-2)
}

onMounted(() => {
  setInterval(updateTime, 5000)
})
</script>

<template>
  <div class="clock-wrapper">
    <div id="clock-main">
        {{ state.time }}
    </div>
    <div id="clock-date">
        {{ state.date }}
    </div>
    <div id="clock-weekday">
        {{ state.weekday }}
    </div>
  </div>
</template>

<style>
.clock-wrapper {
  position: absolute;
  width: 14vw;
  height: 100px;
  left: 4vw;
  text-align: center;
}

#clock-main {
  display: inline;
  font-size: xx-large;
}

#clock-seconds {
  display: inline;
}
</style>

<template>
  <div id="app">
    <h1>Montyhall</h1>
    <div class="form">
      <div v-if="!started">
        <label for="doorsAmount">How many doors?</label>
        <input type="text" id="doorsAmount" size="3" v-model.number="doorsAmount">
      </div>
      <div v-if="!started">
        <label for="selectedDoor">Wich door?</label>
        <input type="text" id="selectedDoor" size="3" v-model.number="selectedDoor">
      </div>
      <button v-if="!started" @click="started = !started">Start</button>
      <button v-if="started" @click="started = !started">Restart</button>
    </div>
    <div v-if="started">
      <div v-for="i in doorsAmount" :key="i">
        <Door />
      </div>
    </div>
  </div>
</template>

<script>
import Door from './components/Door.vue'

export default {
  name: 'App',
  components: { Door },
  data: function () {
    return {
      started: false,
      doorsAmount: 3,
      selectedDoor: false
    }
  }
}
</script>

<style>
* {
    box-sizing: border-box;
    font-family: "Montserrat", sans-serif;
    margin: 0;
}

#app {
  color: #fff;
  background-color: #5c6779;
  width: 100vw;
  height: 100vh;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>

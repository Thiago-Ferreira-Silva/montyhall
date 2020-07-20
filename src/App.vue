<template>
  <div id="app">
    <h1>Montyhall</h1>
    <div class="form">
      <div v-if="!started">
        <label for="doorsAmount">How many doors?</label>
        <input type="text" id="doorsAmount" v-model.number="doorsAmount" />
      </div>
      <div v-if="!started">
        <label for="selectedDoor">Wich door?</label>
        <input type="text" id="selectedDoor" v-model.number="selectedDoor" />
      </div>
      <button v-if="!started" @click="started = !started">Start</button>
      <button v-if="started" @click="started = !started">Restart</button>
    </div>
    <div v-if="started" class="doors">
      <div v-for="i in doorsAmount" :key="i">
        <Door :hasGift="i === selectedDoor" :number="i" />
      </div>
    </div>
  </div>
</template>

<script>
import Door from "./components/Door.vue";

export default {
  name: "App",
  components: { Door },
  data: function() {
    return {
      started: false,
      doorsAmount: 3,
      selectedDoor: 1
    };
  }
};
</script>

<style>
* {
  box-sizing: border-box;
  font-family: "Montserrat", sans-serif;
}

body {
  color: #fff;
  background-color: #5c6779;
}

#app {
  display: flex;
  flex-direction: column;
  align-items: center;
}

#app h1 {
  border: 1px solid #000;
  background-color: #0004;
  padding: 10px;
  margin-bottom: 60px;
}

.form {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  margin-bottom: 40px;
}

.form,
.form input,
.form button {
  margin-bottom: 10px;
  font-size: 2rem;
}

.form input {
  border: solid 3px #aaa;
  border-radius: 20px;
  width: 100px;
  height: 40px;

  background-color: #5c6779;
  color: #fefefe;

  padding: 10px;
  margin-left: 10px;
}

.form button {
  border: solid 3px #aaa;
  border-radius: 20px;
  width: 120px;
  height: 50px;

  background-color: #888;
  color: #fefefe;
}

.doors {
  align-self: stretch;
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
}
</style>

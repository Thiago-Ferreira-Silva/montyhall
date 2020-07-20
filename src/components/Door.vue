<template>
  <div class="door-area">
    <div class="door-frame" :class="{ selected: selected && !open }">
      <Gift v-if="open && hasGift" />
    </div>
    <div class="door" :class="{ open }" @click="selectDoor">
      <div class="number" :class="{ selected: selected && !open }">{{ number }}</div>
      <div class="knob" :class="{ selected: selected && !open }" @click="openDoor"></div>
    </div>
  </div>
</template>

<script>
import Gift from './Gift.vue'

export default {
  name: 'Door',
  components: { Gift },
  props: {
    number: {},
    hasGift: { type: Boolean }
  },
  data: function() {
    return {
      open: false,
      selected: false
    }
  },
  methods: {
    selectDoor() {
      this.selected = !this.selected
    },
    openDoor() {
      this.open = true
    }
  }
}
</script>

<style>
  :root {
    --door-border: 5px solid brown;
    --selected-border: 5px solid yellow;
  }

  .door-area {
    position: relative;

    width: 200px;
    height: 310px;
    margin-bottom: 20px;
    border-bottom: 10px solid #aaa;
    
    display: flex;
    justify-content: center;
  }

  .door-frame {
    position: absolute;
    width: 180px;
    height: 300px;

    border-left: var(--door-border);
    border-top: var(--door-border);
    border-right: var(--door-border);

    display: flex;
    align-items: flex-end;
    justify-content: center;
  }

  .door {
    position: absolute;
    top: 5px;
    width: 170px;
    height: 295px;

    background-color: chocolate;

    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 20px;
  }

  .door .knob {
    width: 20px;
    height: 20px;
    border-radius: 10px;

    background-color: brown;
    align-self: flex-start;
    margin-top: 60px;
  }

  .door .number {
    font-size: 3rem;
  }

  .door-frame.selected {
    border-left: var(--selected-border);
    border-top: var(--selected-border);
    border-right: var(--selected-border);
  }

  .door .number.selected, .door .knob.selected {
    background-color: yellow;
  }

  .door.open {
    background-color: #0007;
  }
  .door.open .number {
    display: none;
  }
  .door.open .knob {
    display: none;
  }
</style>
<template>
  <div class="gift">
    <div class="gift-tie-1"></div>
    <div class="gift-tie-2"></div>
    <div class="gift-top"></div>
    <div class="gift-body"></div>
  </div>
</template>

<script>
export default {
  name: 'Gift'
}
</script>

<style>
  .gift {
    position: relative;
    display: flex;
    flex-direction: column;
    margin-bottom: 70px;
    z-index: 10;
  }

  .gift-tie-1 {
    position: absolute;
    left: 39px;
    width: 10px;
    height: 76px;
    background-color: red;
    z-index: 1;
  }

  .gift-tie-2 {
    position: absolute;
    left: 4px;
    top: 28px;
    width: 80px;
    height: 10px;
    background-color: red;
    z-index: 1;
  }

  .gift-top {
    width: 88px;
    height: 8px;
    background-color: #7aa944;
  }

  .gift-body {
    position: absolute;
    left: 4px;
    top: 8px;
    background-color: #5c7e32;
    width: 80px;
    height: 68px;
  }
</style>
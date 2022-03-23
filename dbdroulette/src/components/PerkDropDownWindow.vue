<template>
  <div class="drop-down-container">
    <p class="drop-down-item">Item</p>
    <p class="drop-down-item">Exhaustion</p>
    <p class="drop-down-item">Healing</p>
    <p class="drop-down-item">Information</p>
    <p class="drop-down-item">Wiggle</p>
    <p class="drop-down-item">Looping</p>
    <p class="drop-down-item">Support</p>
    <p class="drop-down-item">Stealth</p>
    <p class="drop-down-item">Second Chance</p>
    <p class="drop-down-item">Diversion</p>
  </div>
</template>

<style scoped>
  .drop-down-container {
    position: relative;
    display: inline-block;
  }

  .drop-down-item {
    display: none;
    position: absolute;
    background-color: #f1f1f1;
    min-width: 160px;
    box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
    z-index: 1;
  }
</style>
<template>
  <div class="perk-description-window">
    <p class="perk-description">Press Spin to receive your first random perk!</p>
  </div>
</template>

<style scoped>
  .perk-description-window {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  p {
    color: white;
  }

  .drop-down-container {
    position: relative;
    display: block;
  }
  
  .drop-down-item {
    display: flex;
    position: relative;
    background-color: #bbb7b7f6;
    /*background-color: red;*/
    min-width: 160px;
    box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
    /*z-index: 1;*/
    color: black;
    overflow: auto;
  }
</style>
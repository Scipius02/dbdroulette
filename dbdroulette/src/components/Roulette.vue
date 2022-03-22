<template>
  <div class="roulette-window">
    <button>Spin</button>
    <ul>
      <img id="roulette-1"/>
      <img id="roulette-2"/>
      <img id="roulette-3"/>
      <img id="roulette-4"/>
    </ul>
    <button>Reset</button>
  </div>
</template>

<style scoped>
  .roulette-window {
    padding: 2em;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    /*align-content: center;*/
  }

  ul {
    display: flex;
  }

  img {
    margin: 1em;
    min-height: 75px;
    min-width: 75px;
    max-height: 125px;
    max-width: 125px;
    background-color:gray;
  }

  button {
    height: 75px;
    width: 75px;
    background-color:antiquewhite;
  }
</style>

<script>
</script>
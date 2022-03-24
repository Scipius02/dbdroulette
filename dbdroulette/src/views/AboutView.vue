<template>
  <div class="about">
    <h1>DBD Roulette</h1>
    <p>This is a simple app designed to give me some practice with Vue components, routing, and web dev.</p>
    <p>A later version of this app should use dynamic loading of assets from a db.</p>
    <p></p>
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}

.about {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-content: center;
}
</style>

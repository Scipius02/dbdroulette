<script setup>
import { RouterLink, RouterView } from 'vue-router'
import MainTitle from '@/components/MainTitle.vue'
import Perks from '@/components/Perks.vue'
import PerkDescription from '@/components/PerkDescription.vue'
</script>

<script>
  export default {
    name: 'app',
    methods: {
      passCounter(e) {
        this.counter = e;
      }
    }
  }
</script>

<template>
  <div id= "app">
    <div class="main">
      <img alt="DBD logo" class="logo" src="../src/assets/images/Dead-by-Daylight-Logo-700x394.png" width="400" height="220" />

      <div class="wrapper">
        <MainTitle msg="Roulette" />
        <Perks counter='$this.counter' />

        <PerkDescription />

        <nav>
          <!--<RouterLink to="/">Home</RouterLink>-->
          <RouterLink to="/roulette">Survivor Roulette</RouterLink>
          <RouterLink to="/about">About</RouterLink>
          
        </nav>
      </div>
      <RouterView />
      <p hidden @counter = "passCounter"></p>
    </div>
  </div>

  
</template>

<style>
  @import '@/assets/base.css';

  #app {
    max-width: 1280px;
    margin: 0 auto;
    padding: 2rem;

    font-weight: normal;
    
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-content: center;
  }

  .main {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-content: center;
  }
  .wrapper {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-content: center;
  }
  header {
    line-height: 1.5;
    max-height: 100vh;
  }

  .logo {
    display: block;
    margin: 0 auto 2rem;
  }

  a,
  .green {
    text-decoration: none;
    color: hsla(160, 100%, 37%, 1);
    transition: 0.4s;
  }

  .red {
    text-decoration: none;
    color: rgb(184, 3, 3);
    transition: 0.4s;
  }

  @media (hover: hover) {
    a:hover {
      background-color: hsla(160, 100%, 37%, 0.2);
    }
  }

  nav {
    width: 100%;
    font-size: 12px;
    text-align: center;
    margin-top: 2rem;
  }

  nav a.router-link-exact-active {
    color: var(--color-text);
  }

  nav a.router-link-exact-active:hover {
    background-color: transparent;
  }

  nav a {
    display: inline-block;
    padding: 0 1rem;
    border-left: 1px solid var(--color-border);
  }

  nav a:first-of-type {
    border: 0;
  }

  @media (min-width: 1024px) {
    body {
      display: flex;
      place-items: center;
    }

    #app {
      display: grid;
      grid-template-columns: 1fr 1fr;
      padding: 0 2rem;
    }

    header {
      display: flex;
      place-items: center;
      padding-right: calc(var(--section-gap) / 2);
    }

    header .wrapper {
      display: flex;
      place-items: flex-start;
      flex-wrap: wrap;
    }

    .logo {
      margin: 0 2rem 0 0;
    }

    nav {
      text-align: left;
      margin-left: -1rem;
      font-size: 1rem;

      padding: 1rem 0;
      margin-top: 1rem;
    }
  }
</style>

<script setup>
import Roulette from '@/components/Roulette.vue'
</script>

<script>
  export default {
    methods: {
      counterChange(e) {
        console.log(e);
      }
    }
  }
</script>

<template>
  <main>
    <Roulette />
  </main>
</template>

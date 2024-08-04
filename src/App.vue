<script setup>
  import Navbar from '@/components/Navbar.vue'
  import GameList from '@/components/GameList/GameList.vue'
  import { RouterView } from 'vue-router';
</script>

<template>
  <Navbar />
  <RouterView />
</template>
<script setup>
import { RouterView } from 'vue-router'
import NavMenu from './components/NavMenu.vue';
import ProgressBar from './components/ProgressBar.vue';
import FooterMenu from './components/FooterMenu.vue';
</script>

<template>
  <header>
    <NavMenu />
  </header>
  <RouterView />
  <ProgressBar />
  <footer>
    <FooterMenu />
  </footer>
</template>
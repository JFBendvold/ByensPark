<script setup>
import { RouterView } from 'vue-router'
import NavMenu from './components/NavMenu.vue';
import ProgressBar from './components/ProgressBar.vue';
import FooterMenu from './components/FooterMenu.vue';
import { ref } from "vue";

const locked = ref(true);
const userPassword = ref('');

const correctPassword = '12345678';

const unlockSite = () => {
  if (userPassword.value === correctPassword) {
    locked.value = false;
  } else {
    alert('Incorrect password!');
  }
};
</script>

<template>
  <div>
    
    <!-- Show password input if locked -->
    <div v-if="locked" style="cursor: default;">
      <label for="password">Enter password to unlock:</label>
      <input type="password" id="password" v-model="userPassword" style="color: black;" />
      <button @click="unlockSite" style="color: black;">Unlock</button>
    </div>
    
    <!-- Show the site if not locked -->
    <div v-else>
      <header>
        <NavMenu />
      </header>
      <RouterView />
      <ProgressBar />
      <footer>
        <FooterMenu />
      </footer>
    </div>
  </div>
</template>

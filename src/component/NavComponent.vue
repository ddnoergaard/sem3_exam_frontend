<script setup>
import logoImage from '@/assets/logo.png'
import { RouterLink } from 'vue-router'
</script>

<template>
  <nav>
    <RouterLink>
      <img :src="logoImage" alt="" id="logo-img" />
    </RouterLink>
    <div id="link-container">
      <RouterLink id="nav-link-hjem" :to="{ name: home }">Hjem</RouterLink>
      <span id="divider"></span>
      <div id="user-link-container">
        <RouterLink id="nav-link-login" :to="{ name: login }">Login</RouterLink>
      </div>
    </div>
  </nav>
</template>

<style scoped>
nav {
  display: flex;
  height: 10dvh;
  width: 100%;
  justify-content: space-between;
  border-bottom: 1px solid black;
  padding: 0 5dvw;
}

#logo-img {
  height: 100%;
}

#link-container,
#user-link-container {
  display: flex;
  align-items: center;
  height: 100%;
  gap: 1rem;
}

#divider {
  content: '';
  height: 30%;
  width: 1px;
  background-color: black;
}
</style>

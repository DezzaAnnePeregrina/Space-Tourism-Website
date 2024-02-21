<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
    <header>
    <img src="@/assets/images/shared/logo.svg" alt="logo">

      <nav>
        <RouterLink class="li" to="/">00 Home</RouterLink>
        <RouterLink class="li" to="/destination">01 Destination</RouterLink>
        <RouterLink class="li" to="/crew">02 Crew</RouterLink>
        <RouterLink class="li" to="/technology">03 Technology</RouterLink>
      </nav>
      
  </header>
  <RouterView />
</template>

<style scoped>
header{
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: transparent;
  position: absolute;
  top: 0;
  z-index: 9;
  width: 100%;
  padding: 1rem;
  color: aliceblue;
}

nav{
  display: flex;
  gap: 1rem;
}
</style>

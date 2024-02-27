<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
    <header class="flex flex-wrap justify-between items-center pt-8">
      <img class="pl-10" src="@/assets/images/shared/logo.svg" alt="logo">
      <hr>
      <nav class="flex gap-5">
        <RouterLink class="li" :class="{'active':$route.path === '/'}" to="/">00 HOME</RouterLink>
        <RouterLink class="li" :class="{'active':$route.path === '/destination'}" to="/destination">01 DESTINATION</RouterLink>
        <RouterLink class="li" :class="{'active':$route.path === '/crew'}" to="/crew">02 CREW</RouterLink>
        <RouterLink class="li" :class="{'active':$route.path === '/technology'}" to="/technology">03 TECHNOLOGY</RouterLink>
      </nav>
  </header>
  <RouterView />
</template>

<style scoped>
header{
  background-color: transparent;
  position: absolute;
  top: 0;
  width: 100%;
  color: aliceblue;
}

hr{
  height: 1px;
  min-width: 300px;
  width: 600px;
  max-width: 600px;
  position: absolute;
  right: 610px;
  z-index: 1;
}

nav{
  padding: 1rem 6rem 1rem 7rem;
  backdrop-filter: blur(20px);
  background: rgba(255, 255, 255, 0.096);
}

.li{
    font-family: "Poppins", serif;
    font-size: .9rem;
    min-width: 40px;
}
.li.active{
  border-bottom: 1px solid white;
}
</style>

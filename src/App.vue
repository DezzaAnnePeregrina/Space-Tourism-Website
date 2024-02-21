<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
    <header>
      <img src="@/assets/images/shared/logo.svg" alt="logo">
      <hr>
      <nav>
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
  display: flex;
  align-items: center;
  justify-content: space-between;
  background-color: transparent;
  position: absolute;
  top: 0;
  width: 100%;
  padding-top: 2rem;
  color: aliceblue;
}

img{
  padding-left: 3rem;
}

hr{
  height: 1px;
  width: 600px;
  position: absolute;
  right: 610px;
  z-index: 1;
}

nav{
  display: flex;
  gap: 2rem;
  padding: 1rem 6rem 1rem 7rem;
  backdrop-filter: blur(20px);
  background: rgba(255, 255, 255, 0.096);
}

.li{
    font-family: "Poppins", serif;
    font-size: .9rem;
}

.li.active{
  border-bottom: 1px solid white;
}
</style>

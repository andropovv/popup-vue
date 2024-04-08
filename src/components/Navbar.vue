<template>
  <nav class="navbar">
    <RouterLink
      @click="active = 'home'"
      :class="{ active: active == 'home' }"
      to="/"
      >Go to Home
    </RouterLink>
    <RouterLink
      @click="active = 'about'"
      :class="{ active: active == 'about' }"
      to="/about"
      >Go to About</RouterLink
    >
  </nav>
</template>

<script setup>
import { createMemoryHistory, createRouter, RouterLink } from 'vue-router';
import About from './About.vue';
import Home from './Home.vue';
import { ref } from 'vue';

const active = ref('home');

const routes = [
  { path: '/', component: Home },
  { path: '/about', component: About },
];

const router = createRouter({
  history: createMemoryHistory(),
  routes,
});
</script>

<style lang="scss" scoped>
.navbar {
  margin: 0 auto;
  display: flex;
  height: 40px;
  align-items: center;
  justify-content: center;
  gap: 40px;
  width: 100%;

  a {
    text-decoration: none;
    font-size: 18px;
    color: Black;

    &:hover {
      color: blue;
    }
  }

  .active {
    color: gray;
  }
}
</style>

<script setup lang="ts">
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <div class="app">
    <nav>
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </nav>
    <router-view />
  </div>
</template>

<style lang="scss">
.app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;

  nav {
    padding: 1rem;
    text-align: center;
    background: #f8f9fa;
    margin-bottom: 2rem;

    a {
      font-weight: bold;
      color: #2c3e50;
      text-decoration: none;
      margin: 0 0.5rem;

      &.router-link-exact-active {
        color: #42b983;
      }
    }
  }
}
</style>

<template>
  <div class="home">
    <h1>Welcome to Vue Demo</h1>
    <div class="counter">
      <h2>Counter: {{ counter.count }}</h2>
      <h3>Double Count: {{ counter.doubleCount }}</h3>
      <div class="buttons">
        <button @click="counter.increment()">Increment</button>
        <button @click="counter.decrement()">Decrement</button>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { useCounterStore } from '../stores/counter'

const counter = useCounterStore()
</script>

<style scoped lang="scss">
.home {
  padding: 2rem;
  text-align: center;

  h1 {
    color: #2c3e50;
    margin-bottom: 2rem;
  }

  .counter {
    background: #f8f9fa;
    padding: 2rem;
    border-radius: 8px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);

    h2, h3 {
      color: #42b983;
      margin: 1rem 0;
    }

    .buttons {
      display: flex;
      gap: 1rem;
      justify-content: center;
      margin-top: 1rem;

      button {
        padding: 0.5rem 1rem;
        border: none;
        border-radius: 4px;
        background: #42b983;
        color: white;
        cursor: pointer;
        transition: background 0.3s;

        &:hover {
          background: #3aa876;
        }
      }
    }
  }
}
</style> 
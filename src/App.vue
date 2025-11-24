<script setup>
import { ref } from 'vue'
import ProductDisplay from './components/ProductDisplay.vue'
const premium = true
const cart = ref(0)
</script>

<template>
  <div id="app">
    <div class="nav-bar"></div>
    <div class="cart">Cart ({{ cart }})</div>
    <ProductDisplay :premium="premium"></ProductDisplay>
  </div>
</template>

<script setup>
import sockGreen from './assets/images/socks_green.jpeg'
import sockBlue from './assets/images/socks_blue.jpeg'
</script>

<template>
  <div class="product-display">
    <img :src="sockGreen" alt="Green Socks" />
    <img :src="sockBlue" alt="Blue Socks" />
    <div class="product-container">
      <div class="product-info">
        <h1>Socks</h1>
      </div>
    </div>
  </div>
</template>
<script setup>
import sockGreen from './assets/images/socks_green.jpeg'
import sockBlue from './assets/images/socks_blue.jpeg'
const url = "https://sekai.one/piece/saga-8?reprise=true"
const instock = true
</script>

<template>
  <div class="product-display">
    <div class="product-container">
      <div class="product-info">
        <h1>Socks</h1>
        <div class="product-image">
          <img :src="sockGreen" alt="Green Socks" />
        </div>
          <a :href="url" target="_blank" rel="noopener">Va regarder One Piece</a>
          <p v-if="instock">En stock</p>
          <p v-else>En rupture de stock</p>
      </div>
    </div>
  </div>
</template>
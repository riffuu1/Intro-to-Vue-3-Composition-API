<script setup>
import { ref } from 'vue'
import socksGreenImage from './assets/images/socks_green.jpeg'
import socksBlueImage from './assets/images/socks_blue.jpeg'

const product = ref('Socks')
const image = ref(socksGreenImage)
const image2 = ref(socksBlueImage)
const inStock = true
  
const details = ref(['50% cotton', '30% wool', '20% polyester'])

const variants = ref([
  { id: 2234, color: 'green', image: socksGreenImage },
  { id: 2235, color: 'blue',image: socksBlueImage },
])

const cart = ref(0)


function increaseCount(n) {
  cart.value += n
}

function decreaseCount(n) {
  cart.value -= n
}

function updateVariant(variant) {
  image.value = variant.image
}
</script>
  
<template>
  <div class="nav-bar"></div>
  <div class="cart">Cart({{ cart }})</div>
  <div class="product-display">
    <div class="product-container">
      <div class="product-image">    
        <img v-bind:src="image">
      </div>
      <div class="product-info">
        <h1>{{ product }}</h1>
        <p v-if="inStock">In Stock</p>
        <p v-else>Out of Stock</p>
        <ul>
          <li v-for="detail in details">{{ detail }}</li>
        </ul>
        <div class="variant-container">
          <div
              v-for="variant in variants"
              :key="variant.id"
              class="color-circle"
              :style="{ backgroundColor: variant.color }"
              @mouseover="updateVariant(variant)"
          ></div>
        </div>
      <button class=button @click="$emit(increaseCount(1))" >Add to Cart</button>
      <button class=button_remove @click="$emit(decreaseCount(1))" >Remove to Cart</button>
      </div>
    </div>
  </div>
</template>
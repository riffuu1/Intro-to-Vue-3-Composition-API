<script setup>
import sockGreen from './assets/images/socks_green.jpeg'
import sockBlue from './assets/images/socks_blue.jpeg'
const url = "https://sekai.one/piece/saga-8?reprise=true"
const inventaire = 10
const onSale = true
const details = ['50% coton','30% laine', '20% polyester']
const variants = [
  {
    id: 2234,
    color: "green",
    image: sockGreen,
    quantity: 50
  },
  {
    id: 2235,
    color: "blue",
    image: sockBlue,
    quantity: 0
  }
]
const sizes = ['S', 'M', 'L', 'XL']
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
        <p v-if="inventaire > 10">En stock</p>
        <p v-else-if="inventaire >= 1">Faible stock</p>
        <p v-else>En rupture de stock</p>
        <p v-if="onSale">En solde !</p>
      </div>

      <div class="product-details">
        <h2>Composants</h2>
        <ul>
          <li v-for="detail in details" :key="detail">{{ detail }}</li>
        </ul>
      </div>

      <div class="product-variants">
        <h2>Variantes</h2>
        <ul>
          <li v-for="variant in variants" :key="variant.id">
            {{ variant.color }}
          </li>
        </ul>
      </div>
      <div class="product-sizes">
        <h2>Tailles</h2>
        <ul>
          <li v-for="size in sizes" :key="size">
            {{ size }}
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script setup>
import {computed, ref} from "vue";
import socksGreenImage from "@/assets/images/socks_green.jpeg";
import socksBlueImage from "@/assets/images/socks_blue.jpeg";

const product = ref('Socks')
const brand = ref('Vue Mastery')
const selectedVariant = ref(0)

const props = defineProps({
  premium:{
    type: Boolean,
    required: true

  }
})

const details = ref(['50% cotton', '30% wool', '20% polyester'])
const variants = ref([
  { id: 2234, color: 'green', image: socksGreenImage, quantity: 50 },
  { id: 2235, color: 'blue', image: socksBlueImage, quantity: 0 },
])

const cart = ref(0)

const title = computed(() => brand.value + ' ' + product.value)
const image = computed(() => variants.value[selectedVariant.value].image)
const inStock = computed(() => variants.value[selectedVariant.value].quantity > 0)

const addToCart = () => cart.value += 1
const updateVariant = (index) => selectedVariant.value = index

const shipping = computed(()=>{
  return props.premium ? 'Frais de port gratuits' : '5.99 CHF'
})
</script>

<template>
  <div class="product-info">
    <h1>{{ title }}</h1>
    <h2>Shipping: {{shipping}}</h2>
    <p v-if="inStock">In Stock</p>
    <p v-else>Out of Stock</p>
    <p v-if="premium">Frais de port gratuit</p>
    <p v-else></p>
    <ul>
      <li v-for="detail in details" :key="detail">{{ detail }}</li>
    </ul>
    <div
        v-for="(variant, index) in variants"
        :key="variant.id"
        class="color-circle"
        :style="{ backgroundColor: variant.color, border: selectedVariant.value === index ? '2px solid black' : '1px solid #ccc' }"
        @mouseover="updateVariant(index)"
    ></div>
    <button
        class="button"
        :class="{ disabledButton: !inStock }"
        :disabled="!inStock"
        @click="addToCart"
    >
      Add to cart
    </button>
  </div>
</template>
<script setup lang="ts">
</script>
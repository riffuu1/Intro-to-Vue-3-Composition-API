<script setup>
import {ref} from 'vue'

const review = ref({
  name: '',
  content: '',
  rating: null,
  recommand: ''
})

const emit = defineEmits(['review-submitted'])

function onSubmit() {
  // validation
  if (!review.value.name || !review.value.content || !review.value.rating || !review.value.recommand) {
    alert('Merci de remplir tous les champs.')
    return
  }

  // construire l'objet envoyé au parent
  const productReview = {
    name: review.value.name,
    review: review.value.content,
    rating: review.value.rating,
    recommand:review.value.recommand
  }

  // émettre vers le parent
  emit('review-submitted', productReview)

  // reset
  review.value.name = ''
  review.value.content = ''
  review.value.rating = null
  review.value.recommand
}
</script>

<template>
  <form class="review-form" @submit.prevent="onSubmit">
    <h3>Leave a review</h3>

    <label for="name">Name:</label>
    <input id="name" v-model="review.name">

    <label for="review">Review:</label>
    <textarea id="review" v-model="review.content"></textarea>

    <label for="rating">Rating:</label>
    <select id="rating" v-model.number="review.rating">
      <option>5</option>
      <option>4</option>
      <option>3</option>
      <option>2</option>
      <option>1</option>
    </select>
    <label for="rating">Would you recommand it ?</label>
    <select id="recommand" v-model="review.recommand">
      <option value="Yes">OUI</option>
      <option value="No">NON</option>
    </select>

    <input class="button" type="submit" value="Submit">
  </form>
</template>

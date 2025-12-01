<script setup>
defineProps({
  reviews: {
    type: Array,
    required: true
  }
})
</script>

<template>
  <div class="review-container" v-if="reviews.length">
    <h3>Commentaires :</h3>

    <ul>
      <li v-for="(review, index) in reviews" :key="index">
        <p><strong>Nom :</strong> {{ review.name }}</p>
        <p><strong>Note :</strong> {{ review.rating }}</p>
        <p><strong>Commentaire :</strong> {{ review.review }}</p>
        <p><strong>A recommander :</strong> {{review.recommand}}</p>
      </li>
    </ul>
  </div>
</template>

<style scoped>
.review-container {
  margin-top: 20px;
}
</style>

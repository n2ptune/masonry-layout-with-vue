<template>
  <div class="wrapper">
    <div class="heading">
      <h1>Masonry Layout Design Examples</h1>
    </div>
    <div class="cards">
      <image-card v-for="image in images" :key="image.id" :image="image" />
    </div>
  </div>
</template>

<script>
export default {
  components: {
    ImageCard: () => import('@/components/ImageCard.vue')
  },

  props: {
    images: {
      type: Array,
      required: true
    }
  }
}
</script>

<style scoped>
.wrapper {
  margin-top: 5rem;
}
.heading h1 {
  text-align: center;
  padding: 0 1rem;
}
.wrapper div {
  margin: 3rem auto;
}
.wrapper .cards {
  max-width: var(--card-container-width);
}
</style>

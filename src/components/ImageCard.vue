<template>
  <div class="card">
    <img :src="image.urls.small" class="image" />
    <div class="meta">
      {{ image.id }}
    </div>
  </div>
</template>

<script>
export default {
  props: {
    image: {
      type: Object,
      required: true
    }
  },

  created() {
    console.log(this.image)
  },

  mounted() {
    this.$el.style.gridRowEnd = `span ${Math.floor(
      (this.$el.children[0].height + this.$el.children[1].clientHeight) / 9
    )}`
    // let images = document.querySelectorAll('.card')
    // for (let i = 0; i < images.length; i++) {
    //   console.log(images[i])
    //   images[i].style.gridRowEnd = `span ${Math.floor(
    //     images[i].children[0].height / 10
    //   )}`
    // }
  }
}
</script>

<style scoped>
.card {
  margin: 0.5rem;
}
.meta {
}
.image {
  border-radius: 10px;
}
</style>

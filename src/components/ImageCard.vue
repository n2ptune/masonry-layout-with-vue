<template>
  <div class="card">
    <img :src="image.urls.small" class="image" @load="resizeBlock" />
    <div class="meta">
      <div class="rank">
        likes {{ image.likes }} download {{ image.downloads }}
      </div>
      <div class="line">views {{ image.views }}</div>
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

  methods: {
    resizeBlock() {
      const el = this.$el
      const imageHeight = el.children[0].height
      const metaHeight = el.children[1].clientHeight

      el.style.gridRowEnd = `span ${Math.floor(
        (imageHeight + metaHeight) / 10
      )}`
    }
  },

  created() {
    console.log(this.image)
  }
}
</script>

<style scoped>
.card {
  /* margin: 0.5rem; */
}
.image {
  border-radius: 10px;
}
</style>

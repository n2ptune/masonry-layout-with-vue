<template>
  <div
    class="card"
    :style="{
      height: tH + 'px',
      gridRowEnd: gap,
      backgroundColor: 'gray',
      borderRadius: '10px'
    }"
  >
    <div class="image">
      <img
        :src="image.urls.small"
        class="image"
        @load="resizeBlock"
        :style="{ width: '100%' }"
      />
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

  data: () => ({
    gap: null,
    tH: null
  }),

  created() {
    this.tH = Math.round(this.image.height / (this.image.width / 400))
    const gap = Math.round(this.tH / 10)
    this.gap = `span ${gap}`
  },

  methods: {
    resizeBlock() {}
  }
}
</script>

<style scoped>
.image {
  border-radius: 10px;
  height: inherit;
}
</style>

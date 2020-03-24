<template>
  <div class="card" :style="{ gridRowEnd: gap, overflow: 'hidden' }">
    <div class="image" :style="{ width: '100%', overflow: 'hidden' }">
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
    gap: null
  }),

  methods: {
    resizeBlock() {
      const el = this.$el
      const elHeight = el.children[0].offsetHeight
      const gap = Math.floor(elHeight / 15)

      this.gap = `span ${gap}`
    }
  }
}
</script>

<style scoped>
.image {
  border-radius: 10px;
}
</style>

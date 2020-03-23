<template>
  <div class="app">
    <image-card-list :images="images" />
  </div>
</template>

<script>
const DEFAULT_IMAGES_COUNT = 30

export default {
  data: () => ({
    images: []
  }),

  components: {
    ImageCardList: () => import('@/components/ImageCardList.vue')
  },

  methods: {
    /**
     * @param {number} count
     */
    async getRandomImages(count) {
      try {
        const { data } = await this.axios.get(
          process.env.VUE_APP_URL + '/photos/random',
          {
            headers: {
              Authorization: 'Client-ID ' + process.env.VUE_APP_ACCESS_KEY
            },
            params: {
              count
            }
          }
        )
        // Binding data to this component data
        this.images = data
      } catch (error) {
        console.error(error)
      }
    },
    async getRandomImagesFromLocal() {
      try {
        const { default: localData } = await import('@/assets/test_data.json')
        this.images = localData
      } catch (err) {
        console.error(err)
      }
    }
  },

  async created() {
    if (process.env.NODE_ENV === 'production') {
      await this.getRandomImages(DEFAULT_IMAGES_COUNT)
    } else {
      await this.getRandomImagesFromLocal()
    }
  }
}
</script>

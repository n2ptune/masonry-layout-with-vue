<template>
  <div class="card"></div>
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
  }
}
</script>

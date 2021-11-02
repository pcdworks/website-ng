<template>
  <v-carousel
    v-model="model"
    hide-delimiters
    class="mb-4"
    show-arrows-on-hover
  >
    <v-carousel-item
      v-for="(image, i) in images"
      :key="i"
      :src="image.src"
    >
    <v-container
      fill-height
      fluid
      pa-0 ma-0 pb-0
      v-if="image.text"
    >
      <v-layout fill-height align-end pb-0 mb-0>
        <v-flex xs12>
          <v-card class="pa-5 tinted-black">
          <span class="headline white--text" v-text="image.text"></span>
          </v-card>
        </v-flex>
      </v-layout>
    </v-container>
    </v-carousel-item>
  </v-carousel>
</template>

<script>
export default {
  props: {
    images: {
      type: Array,
      default: () => {return []}
    }
  },
  data: () => ({
    model: 0
  }),
}
</script>

<style scoped>
.tinted-black {
  background: rgba(0, 0, 0, 0.3);
}
</style>
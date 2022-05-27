<template>
  <v-carousel v-model="model">
    <v-carousel-item
      v-for="(image, i) in images"
      :key="i"
      :src="getSource(image)"
    >
    <v-container
      v-if="image.text"
      fill-height
      fluid
      pa-0 ma-0 pb-0
    >
      <v-layout fill-height align-end pb-0 mb-0>
        <v-flex xs12>
          <v-card class="pa-5 tinted-black">
          <span class="headline white--text" v-text="getText(image)"></span>
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
  methods: {
    getSource(image) {
      if (typeof(image) === 'string') {
        return image
      } else {
        return image.link
      }
    },
    getText(image) {
        if (typeof(image) === 'object') {
          return image.text
      } else {
        return ''
      }
    }
  }
}
</script>

<style scoped>
.tinted-black {
  background: rgba(0, 0, 0, 0.3);
}
</style>
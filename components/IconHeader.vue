<template>
  <v-card-title>
    <v-img
      :src="image"
      max-height="150px"
      max-width="150px"
      class="icon-image"
    ></v-img>
    <div class="icon-title">{{ text }}</div>
  </v-card-title>
</template>

<script>
export default {
  name: 'IconHeader',
  props: {
    image: {
      type: String,
      default: '',
    },
    text: {
      type: String,
      default: '',
    },
  },
}
</script>

<style lang="scss" scoped>
.icon-image {
  display: inline-block;
  max-width: 40%;
}

.icon-title {
  color: #afbc21;
  font-size: 2.2rem;
  font-weight: 600;
  padding-left: 1rem;
  max-width: calc(60% - 1rem);
  display: inline-block;
  white-space: normal;
  word-break: break-word;
}

@media #{map-get($display-breakpoints, 'sm-and-down')} {
  .icon-image {
    display: block;
    max-width: 100vw;
    margin: 0 auto;
  }

  .icon-title {
    padding-top: 1rem;
    text-align: center;
    max-width: 100vw;
    width: 100vw;
    display: block;
    white-space: normal;
    word-break: break-word;
  }
}
</style>
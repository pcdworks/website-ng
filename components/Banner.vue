<template>
<nuxt-link :to="path">
    <v-banner
    :color="color"
    :elevation="elevation"
    :icon="icon"
    >
        {{message}}
        <br/>
        <v-btn
            v-if="button == 'true'"
            class="float-right"
            :to="path"
            :color="buttonColor"
            >
                {{buttonText}}
            </v-btn>
    </v-banner>
</nuxt-link>
</template>

<script>
export default {
  name: 'Banner',
  props: {
      message: {
          type: String,
          default: ''
      },
      icon: {
          type: String,
          default: ''
      },
      color: {
          type: String,
          default: 'primary'
      },
      elevation:{
          type: String,
          default: "5"
      },
      path: {
          type: String,
          default: '/'
      },
      button: {
          type: String,
          default: 'false'
      },
      buttonText: {
          type: String,
          default: ''
      },
      buttonColor: {
          type: String,
          default: 'accent'
      }
    },
  data: () => ({
  }),
  methods: {
  }
}
</script>

<style scoped>
a {
    text-decoration: none !important;
}
</style>
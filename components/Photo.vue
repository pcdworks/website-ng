<template>
<!-- start, center, end -->
  <v-row :justify="justify" class="pa-3 mb-2">
    <v-img
      :src="src"
      lazy-src="/images/loader.jpg"
      :max-width="maxWidth"
      :max-height="maxHeight"
    >
      <template #placeholder>
        <v-row
          class="fill-height ma-0"
          align="center"
          justify="center"
        >
          <v-progress-circular
            indeterminate
            color="grey lighten-5"
          ></v-progress-circular>
        </v-row>
      </template>
    </v-img>
  </v-row>
</template>

<script>
export default {
  props: {
    src: {
      type: String,
      default: ''
    },
    justify: {
      type: String,
      default: 'start'
    },
    maxWidth: {
      type: String,
      default: '100%'
    },
    maxHeight: {
      type: String,
      default: '50%'
    }
  },
  data: () => ({
  }),
}
</script>

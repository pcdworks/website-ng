<template>
  <v-hover v-slot="{ hover }">
    <v-card
      max-width="600"
    >
      <v-img
        :aspect-ratio="16/9"
        :src="src"
      >
        <v-expand-transition>
          <div
            v-if="hover"
            class="d-flex transition-fast-in-fast-out primary v-card--reveal black--text"
            style="height: 100%;"
          >
          <p class="pa-5">
            {{text}}
          </p>
          </div>
        </v-expand-transition>
      </v-img>
    </v-card>
  </v-hover>
</template>

<script>
export default {
  props: {
    src: {
      type: String,
      default: ''
    },
    text: {
      type: String,
      default: ''
    }
  },
  data: () => ({
  })
}
</script>

<style>

.v-card--reveal {
  align-items: center;
  bottom: 0;
  justify-content: center;
  opacity: 0.9;
  position: absolute;
  width: 100%;
}

</style>
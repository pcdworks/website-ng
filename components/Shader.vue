<template>
  <v-hover v-slot="{ hover }">
    <v-card class="mb-8">
      <v-img :aspect-ratio="16 / 9" :src="src" max-height="300px">
        <v-expand-transition>
          <div
            v-if="hover"
            class="
              d-flex
              transition-fast-in-fast-out
              primary
              v-card--reveal
              black--text
            "
            style="height: 100%"
          >
            <div
              v-resize-text="{
                ratio: 3.5,
                minFontSize: '12px',
                maxFontSize: '26px',
                delay: 200,
              }"
              class="pa-5"
            >
              {{ text }}
            </div>
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
      default: '',
    },
    text: {
      type: String,
      default: '',
    },
  },
  data: () => ({}),
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
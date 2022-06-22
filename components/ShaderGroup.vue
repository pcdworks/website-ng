<template>
  <v-row class="fill-height" align="center" justify="center">
    <template v-for="(item, i) in items">
      <v-col :key="i" cols="12" md="4">
        <shader :src="item.src" :text="item.text"></shader>
      </v-col>
    </template>
  </v-row>
</template>

<script>
import Shader from './Shader.vue'
export default {
  components: { Shader },
  props: {
    items: {
      type: Array,
      default: () => {
        return []
      },
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
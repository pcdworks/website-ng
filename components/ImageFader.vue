<template>
  <v-img :src="image" class="fader">
    <v-container fluid fill-height class="fader-box">
      <v-row>
        <v-col class="fader-content">
          <slot></slot>
        </v-col>
      </v-row>
    </v-container>
  </v-img>
</template>

<script>
export default {
  name: 'ImageFader',
  props: {
    image: {
      type: String,
      default: '',
    },
  },
}
</script>

<style scoped>
.fader-box {
  background: rgba(51, 102, 51, 0.5);
}

.fader-content {
  color: rgba(255, 255, 255, 1);
  font-size: 1.6rem;
}

.fader {
  min-height: 580px;
  text-align: center;
  color: white;
  font-weight: 600;
}
</style>
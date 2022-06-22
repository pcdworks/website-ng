<template>
  <v-img :src="image" class="fader" :aspect-ratio="24 / 9">
    <v-container fluid fill-height class="fader-box">
      <v-row>
        <v-col class="fader-content">
          <div class="pa-2 py-16 px-xl-16 px-lg-16 px-md-4">
            <div class="px-xl-16 px-lg-16 px-md-4">
              <slot></slot>
            </div>
          </div>
        </v-col>
      </v-row>
    </v-container>
  </v-img>
</template>

<script>
export default {
  name: 'ImageSlide',
  props: {
    image: {
      type: String,
      default: '',
    },
  },
}
</script>

<style lang="scss" scoped>
.fader-box {
  background: rgba(0, 0, 0, 0.7);
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
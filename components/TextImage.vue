<template>
  <div class="py-16 px-xl-16 px-lg-16 px-md-4">
    <v-row class="px-xl-16 px-lg-16 px-md-4">
      <v-col cols="12" xl="6" lg="6" md="6" :order="primaryOrder">
        <div class="pa-4 mx-4">
          <slot name="primary"></slot>
        </div>
      </v-col>
      <v-col cols="12" xl="6" lg="6" md="6" :order="extraOrder">
        <div class="pt-4 px-4 px-xl-16 px-lg-4 px-md-4 px-sm-16">
          <div :class="trimClass">
            <image-viewer
              v-if="images.length === 0"
              :image="image"
              class="align-end"
              contain
            >
              <div
                v-if="extra"
                class="
                  extra-content
                  py-2
                  px-2
                  py-lg-10
                  px-lg-16
                  py-xl-10
                  px-xl-16
                  py-md-8
                  px-md-6 px-sm-6
                  py-sm-6
                "
              >
                <slot name="extra"></slot>
              </div>
            </image-viewer>
            <carousel v-else :images="images"> </carousel>
          </div>
        </div>
      </v-col>
    </v-row>
  </div>
</template>

<script>
import ImageViewer from './ImageViewer.vue'
import Carousel from './Carousel.vue'
export default {
  name: 'TextImage',
  components: { ImageViewer, Carousel },
  props: {
    image: {
      type: String,
      default: '',
    },
    images: {
      type: Array,
      default: () => [],
    },
    trim: {
      type: Boolean,
      default: false,
    },
    extra: {
      type: Boolean,
      default: false,
    },
    order: {
      type: String,
      default: 'ti',
    },
  },
  data() {
    return {}
  },
  computed: {
    trimClass() {
      if (this.trim) {
        return 'trim'
      }
      return ''
    },
    primaryOrder() {
      if (this.order === 'it') {
        return 2
      } else {
        return 1
      }
    },
    extraOrder() {
      if (this.order === 'it') {
        return 1
      } else {
        return 2
      }
    },
  },
}
</script>

<style lang="scss" scoped>
.trim {
  background: linear-gradient(90deg, rgba(255, 255, 255, 0) 50%, #5e6e64 50%);
  padding-top: 3rem;
  padding-bottom: 3rem;
  padding-right: 3rem;
}

::v-deep p,
ul {
  font-weight: 500;
  color: #5e6e64;
}

::v-deep h1,
::v-deep h2,
::v-deep h3 {
  color: #afbc21;
}

::v-deep .extra-content {
  background: rgba(51, 102, 51, 0.8);
  color: rgba(255, 255, 255, 1);
  font-size: 1.3rem;
  h2 {
    color: inherit;
    font-size: 2rem;
  }
}

@media #{map-get($display-breakpoints, 'md-and-down')} {
  ::v-deep .extra-content {
    background: rgba(51, 102, 51, 0.8);
    color: rgba(255, 255, 255, 1);
    font-size: 1rem;
    h2 {
      color: inherit;
      font-size: 1.2rem;
    }
  }

  .trim {
    padding: 1.5rem;
  }
}
</style>
<template>
  <div class="py-8 px-0">
    <v-row class="px-0">
      <v-col cols="12" xl="8" lg="8" md="8" class="full-height back">
        <div class="pa-2 py-10 px-xl-16 px-lg-16 px-md-4">
          <div class="mx-4 px-xl-16 px-lg-16 px-md-4">
            <slot name="left"></slot>
          </div>
        </div>
      </v-col>
      <v-col cols="12" xl="4" lg="4" md="4">
        <div :class="trimClass">
          <image-viewer
            v-if="images.length === 0"
            :image="image"
            class="align-end"
            :aspect-ratio="1"
          >
            <div
              v-if="hasRight"
              class="
                right-content
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
              <slot name="right"></slot>
            </div>
          </image-viewer>
          <carousel v-else :images="images"> </carousel>
        </div>
      </v-col>
    </v-row>
  </div>
</template>

<script>
import ImageViewer from './ImageViewer.vue'
import Carousel from './Carousel.vue'
export default {
  name: 'TextImageTint',
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
  },
  data() {
    return {
      carousel: 0,
    }
  },
  computed: {
    hasRight() {
      return this.$slots.default[0].text.length > 4
    },
    trimClass() {
      if (this.trim) {
        return 'trim'
      }
      return ''
    },
  },
}
</script>

<style lang="scss" scoped>
.back {
  background: #5e6e64;
}
.trim {
  background: linear-gradient(90deg, rgba(255, 255, 255, 0) 50%, #5e6e64 50%);
  padding-top: 3rem;
  padding-bottom: 3rem;
  padding-right: 3rem;
}

::v-deep p,
ul {
  font-size: 1.2rem;
  font-weight: 500;
  color: white;
  padding-left: 1rem;
  padding-right: 1rem;
}

::v-deep h1 {
  text-transform: uppercase;
  color: white;
  font-size: 4.5rem;
  line-height: 1.1;
  padding-left: 1rem;
  padding-right: 1rem;
}

::v-deep h2 {
  color: white;
  font-size: 3rem;
  padding-left: 1rem;
  padding-right: 1rem;
}

::v-deep .right-content {
  background: rgba(51, 102, 51, 0.8);
  color: rgba(255, 255, 255, 1);
  font-size: 1.3rem;
  h2 {
    color: inherit;
    font-size: 2rem;
  }
}

@media #{map-get($display-breakpoints, 'md-and-down')} {
  ::v-deep h1 {
    font-size: 3rem;
  }

  ::v-deep h2 {
    font-size: 2rem;
  }

  ::v-deep .right-content {
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
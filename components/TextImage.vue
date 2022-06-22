<template>
  <div :class="outerClass">
    <v-row :class="rowClass">
      <v-col
        cols="12"
        :xl="primarySize"
        :lg="primarySize"
        :md="primarySize"
        :order="primaryOrder"
        :class="tintClass"
      >
        <div :class="padContentClass">
          <slot name="primary"></slot>
        </div>
      </v-col>
      <v-col
        cols="12"
        :xl="extraSize"
        :lg="extraSize"
        :md="extraSize"
        :order="extraOrder"
      >
        <div :class="padImageClass">
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
    tint: {
      type: Boolean,
      default: false,
    },
    third: {
      type: Boolean,
      default: false,
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
    primarySize() {
      if (this.third) {
        return 8
      }
      return 6
    },
    extraSize() {
      if (this.third) {
        return 4
      }
      return 6
    },
    tintClass() {
      if (this.tint) {
        return 'tint full-height'
      }
      return ''
    },
    outerClass() {
      if (this.tint) {
        return 'py-8 px-0'
      }
      return 'py-16 px-xl-16 px-lg-16 px-md-4'
    },
    rowClass() {
      if (this.tint) {
        return 'px-0'
      }
      return 'px-xl-16 px-lg-16 px-md-4'
    },
    padImageClass() {
      if (this.tint) {
        return ''
      }
      return 'pt-4 px-4 px-xl-16 px-lg-4 px-md-4 px-sm-16'
    },
    padContentClass() {
      if (this.tint) {
        return 'mx-4 px-xl-16 px-lg-16 px-md-4 py-10'
      }
      return 'pa-4 mx-4'
    },
  },
}
</script>

<style lang="scss" scoped>
.tint {
  background: #5e6e64;
}

.tint ::v-deep h1,
.tint ::v-deep h2,
.tint ::v-deep h3,
.tint ::v-deep p,
.tint ::v-deep ul {
  color: white;
}

.trim {
  background: linear-gradient(90deg, rgba(255, 255, 255, 0) 50%, #5e6e64 50%);
  padding-top: 3rem;
  padding-bottom: 3rem;
  padding-right: 3rem;
}

::v-deep p,
::v-deep ul {
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
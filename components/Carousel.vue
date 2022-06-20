<template>
  <v-row justify="center">
    <v-dialog
      v-model="dialog"
      fullscreen
      transition="dialog-bottom-transition"
    >
      <template #activator="{ on, attrs }">
        <v-carousel v-model="model">
          <v-carousel-item
            v-for="(image, i) in images"
            :key="i"
            :src="getSource(image)"
             v-bind="attrs" v-on="on"
          >
          <v-container
            v-if="image.text"
            fill-height
            fluid
            pa-0 ma-0 pb-0
          >
            <v-layout fill-height align-end pb-13 mb-0>
              <v-flex xs12>
                <v-card class="pa-5 tinted-black">
                  <!-- eslint-disable vue/no-v-html -->
                  <span id="tinted" class="headline" v-html="getText(image)"></span>
                  <!--eslint-enable-->
                </v-card>
              </v-flex>
            </v-layout>
          </v-container>
          </v-carousel-item>
        </v-carousel>
      </template>
      <v-card>
          <v-toolbar
            color=""
            >
            <v-toolbar-title>{{getAlt(currentImage)}}</v-toolbar-title>
            <v-spacer></v-spacer>
            <v-toolbar-items>
                <v-btn
                    icon
                    @click="dialog = false"
                >
                    <v-icon>mdi-close</v-icon>
                </v-btn>
            </v-toolbar-items>
            </v-toolbar>
        <v-img class="ma-2" max-height="calc(100vh - 64px - 16px)" max-width="100vw" :src="getSource(currentImage)" contain></v-img>
      </v-card>
    </v-dialog>
  </v-row>
</template>

<script>
import { marked } from 'marked'

export default {
  props: {
    images: {
      type: Array,
      default: () => {return []}
    }
  },
  data: () => ({
    model: 0,
    dialog: false
  }),
  computed: {
    currentImage () {
      return this.images[this.model]
    }
  },
  methods: {
    getSource(image) {
      if (typeof(image) === 'string') {
        return image
      } else {
        return image.link
      }
    },
    getText(image) {
        if (typeof(image) === 'object' && image.text) {
          return marked.parse(image.text)
      } else {
        return ''
      }
    },
    getAlt(image) {
        if (typeof(image) === 'object' && image.alt) {
          return image.alt
      } else {
        return 'Image Viewer'
      }
    }
  }
}
</script>

<style lang="scss" scoped>
.tinted-black {
  background: rgba(0, 0, 0, 0.3);
}

#tinted ::v-deep h1 {
  font-size: 1.8rem;
  color: rgba(255,255,255,1);
}

#tinted ::v-deep h2 {
  font-size: 1.5rem;
  color: rgba(255,255,255,1);
}

#tinted ::v-deep h3 {
  font-size: 1.2rem;
  color: rgba(255,255,255,1);
}

#tinted ::v-deep p,
#tinted ::v-deep ul {
  font-size: 1rem;
  color: rgba(255,255,255,1);
}

@media #{map-get($display-breakpoints, 'md-and-down')} {

#tinted ::v-deep h1 {
  font-size: 1.3rem;
}

#tinted ::v-deep h2 {
  font-size: 1.1rem;
}

#tinted ::v-deep h3 {
  font-size: 0.9rem;
}

#tinted ::v-deep p,
#tinted ::v-deep ul {
  font-size: 0.7rem;
}

}
</style>
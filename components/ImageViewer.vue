<template>
  <v-row justify="center">
    <v-dialog
      v-model="dialog"
      fullscreen
      transition="dialog-bottom-transition"
    >
      <template v-slot:activator="{ on, attrs }">
        <v-img v-bind="attrs" v-on="on" :src="image" class="align-end" :aspect-ratio="1" contain>
        </v-img>
      </template>
      <v-card>
          <v-toolbar
            color=""
            >
            <v-toolbar-title>Image Viewer</v-toolbar-title>
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
        <v-img max-height="calc(100vh - 64px)" max-width="100vw" :src="image" contain>
        </v-img>
      </v-card>
    </v-dialog>
  </v-row>
</template>

<script>
  export default {
    name: 'ImageViewer',
    props: {
        image: {
            type: String,
            default: ''
        }
    },
    data () {
      return {
        dialog: false,
      }
    },
  }
</script>
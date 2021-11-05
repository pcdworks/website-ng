<template>
  <v-timeline :dense=dense>
    <v-timeline-item
      v-for="(n, i) in timeline"
      :key="i"
      color="primary"
      large
      >
      <v-card class="elevation-2">
        <v-card-title class="timeline-headline">
          {{n.date}}
        </v-card-title>
        <v-card-text>
          <br/>
          <div v-html="$md.render(n.text)"></div>
        </v-card-text>
      </v-card>
    </v-timeline-item>
  </v-timeline>
</template>

<script>
export default {
  props: {
    timeline: {
      type: Array,
      default: () => { return [] },
    }
  },
  data: () => {
    return {
      dense: false,
      windowWidth: 0,
      windowHeight: 0
    }
  },
  mounted() {
    this.$nextTick(function() {
      window.addEventListener('resize', this.getWindowWidth);
      window.addEventListener('resize', this.getWindowHeight);

      /* Init */
      this.getWindowWidth()
      this.getWindowHeight()
    })
  },
  methods: {
    getWindowWidth(event) {
      this.windowWidth = document.documentElement.clientWidth;
      this.dense = this.windowWidth < 500;
    },
    getWindowHeight(event) {
      this.windowHeight = document.documentElement.clientHeight;
    }
  }
}
</script>

<style>
.timeline-headline {
  background: #afbd21;
}
</style>

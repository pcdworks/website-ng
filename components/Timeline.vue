<template>
  <v-timeline class="timeline px-md-6 px-sm-4 px-4" :dense="dense">
    <v-timeline-item v-for="(item, n) in timeline" :key="n" large>
      <template #icon>
        <v-avatar class="avatar">
          <img :src="item.image" />
        </v-avatar>
      </template>
      <template #opposite>
        <span>{{item.opposite}}</span>
      </template>
      <v-card class="elevation-4">
        <v-card-text>
            <!-- eslint-disable vue/no-v-html -->
            <div v-html="contentHTML(item.primary)"></div>
            <!--eslint-enable-->
        </v-card-text>
      </v-card>
    </v-timeline-item>
  </v-timeline>
</template>


<script>
import { marked } from 'marked'
export default {
  name: 'Timeline',
  props: {
    timeline: {
      type: Array,
      default: () => [],
    },
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
  beforeDestroy() {
    window.removeEventListener('resize', this.getWindowWidth);
    window.removeEventListener('resize', this.getWindowHeight);
  },
  methods: {
    getWindowWidth(event) {
      this.windowWidth = document.documentElement.clientWidth;
      this.dense = this.windowWidth < 960;
    },
    getWindowHeight(event) {
      this.windowHeight = document.documentElement.clientHeight;
    },
    contentHTML(markdown) {
      return marked.parse(markdown)
    }
  }

}
</script>

<style lang="scss" scoped>
.timeline {
  position: relative;
  background: white;
}

.avatar {
  background: white;
}

  ::v-deep h1 {
    font-size: 1.7rem;
  }

  ::v-deep h2 {
    font-size: 1.5rem;
  }

  ::v-deep h3 {
    font-size: 1.3rem;
  }

  ::v-deep p,
  ::v-deep ul {
    font-size: 1rem;
  }
</style>

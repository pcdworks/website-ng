<template>
  <v-timeline class="timeline" :dense="false">
    <v-timeline-item v-for="(item, n) in timeline" :key="n" large>
      <template #icon>
        <v-avatar>
          <img :src="item.image" />
        </v-avatar>
      </template>
      <template #opposite>
        <span>{{item.opposite}}</span>
      </template>
      <v-card class="elevation-2">
        <v-card-title class="text-h5"> Lorem ipsum </v-card-title>
        <v-card-text>
            {{item.primary}}
        </v-card-text>
      </v-card>
    </v-timeline-item>
  </v-timeline>
</template>


<script>
export default {
  name: 'Timeline',
  props: {
    timeline: {
      type: Array,
      default: () => [],
    },
  },
}
</script>

<style lang="scss" scoped>
.timeline {
  position: relative;
}
</style>

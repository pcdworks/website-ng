<template>
  <v-card elevation="0" class="pt-6 pb-6 fill-height" flat>
    <icon-header :image="image" :text="title"></icon-header>
    <v-card-subtitle>
      <div class="phase-subtitle">{{ subtitle }}</div>
    </v-card-subtitle>
    <v-card-text>
      <ul class="phase-text pr-16">
        <div v-for="(item, idx) in bullets" :key="idx">
          <li v-if="typeof item == 'string'">{{ item }}</li>
          <ul v-else>
            <li v-for="(itm, ix) in item" :key="ix">
              {{ itm }}
            </li>
          </ul>
        </div>
      </ul>
    </v-card-text>
  </v-card>
</template>

<script>
import IconHeader from './IconHeader.vue'
export default {
  name: 'Phase',
  components: { IconHeader },
  props: {
    image: {
      type: String,
      default: '',
    },
    title: {
      type: String,
      default: '',
    },
    subtitle: {
      type: String,
      default: '',
    },
    bullets: {
      type: Array,
      default: () => {},
    },
  },
}
</script>

<style lang="scss" scoped>
.phase-image {
  float: left;
  max-width: 40%;
}

.phase-title {
  color: #afbc21;
  font-size: 2.4rem;
  font-weight: 600;
  padding-left: 1rem;
  width: 50%;
  float: right;
}

.phase-subtitle {
  padding-top: 3rem;
  color: black;
  font-size: 1.7rem;
  font-weight: 600;
}

.phase-text {
  color: #5e6e64;
  font-size: 1rem;
  font-weight: 600;
}
</style>
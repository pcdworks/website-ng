<template>
  <div class="mb-5">
    <div  class="map-responsive">
      <iframe :src="src"
              frameborder="0"
              style="border:0;"
              allowfullscreen="">
      </iframe>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    src: {
      type: String,
      default: ''
    }
  },
  data: () => ({
  }),
}
</script>

<style scoped>
.map-responsive {
  overflow:hidden;
  padding-bottom: 40.25%;
  position: relative;
  height: 0;
}

.map-responsive iframe {
  left: 0;
  top: 0;
  height: 100%;
  width: 100%;
  position: absolute;
}
</style>
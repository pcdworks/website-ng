<template>
  <div>
    <div class="videoWrapper">
      <iframe :src="src"
              frameborder="0"
              allow="accelerometer;
                    autoplay;
                    encrypted-media;
                    gyroscope;
                    picture-in-picture"
                    allowfullscreen>
      </iframe>
    </div>
    <div class="below-text">
      {{text}}
    </div>
  </div>
</template>


<script>
export default {
  props: {
    src: {
      type: String,
      default: '',
    },
    text: {
      type: String,
      default: '',
    },
  },
  data: () => ({}),
}
</script>

<style scoped>
.below-text {
  text-align: center;
  padding-top: 3px;
}

.videoWrapper {
    position: relative;
    padding-bottom: 56.25%; /* 16:9 */
    padding-top: 25px;
    height: 0;
}
.videoWrapper iframe {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
}

</style>
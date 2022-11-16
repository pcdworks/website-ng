<template>
    <div class="videoWrapper my-6 mx-4 mx-sm-8 mx-md-12">
      <iframe
        :src="link"
        frameborder="0"
        allow="accelerometer;
                    autoplay;
                    encrypted-media;
                    gyroscope;
                    picture-in-picture"
        allowfullscreen
      >
      </iframe>
    </div>
</template>

<script>
export default {
  name: 'YouTubeFull',
  props: {
    link: {
      type: String,
      default: '',
    },
  },
}
</script>

<style lang="scss" scoped>

::v-deep h1,
::v-deep h2,
::v-deep h3,
::v-deep h4,
::v-deep p,
::v-deep ul {
  color: white;
}

.videoWrapper {
  position: relative;
  padding-bottom: 56.25%; /* 16:9 */
  padding-top: 25px;
  height: 0;
}
.videoWrapper iframe {
  position: absolute;
  padding: 0px;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  border-radius: 15px;
  box-shadow: 0px 0px 10px #fff;
}

.videoWrapper iframe:hover {
  box-shadow: 0px 0px 20px #fff;
}
</style>
<template>
  <div class="backing">
    <v-row align="center">
      <v-col class="mx-lg-16 px-lg-16" align-self="center">
        <div class="mx-lg-16 px-lg-16">
          <div class="videoWrapper my-6 mx-4 mx-sm-8 mx-md-12">
            <iframe :src="link"
                    frameborder="0"
                    allow="accelerometer;
                          autoplay;
                          encrypted-media;
                          gyroscope;
                          picture-in-picture"
                          allowfullscreen>
            </iframe>
          </div>
        </div>
        <br>
        <slot></slot>
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
    name: 'YouTube',
    props: {
      link: {
          type: String,
          default: ""
      }
    }
}
</script>

<style scoped>

.backing {
  background: #1f1f1f;
  position: relative;
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
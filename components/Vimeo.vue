<template>
  <div>
    <div class="embed-container">
      <iframe
        :src="link"
        frameborder="0"
        webkitAllowFullScreen
        mozallowfullscreen
        allowFullScreen
      >
      </iframe>
    </div>
    <div class="below-text">
      {{ text }}
    </div>
  </div>
</template>

<style scoped>
.below-text {
  text-align: center;
  padding-top: 3px;
}

.embed-container {
  position: relative;
  padding-bottom: 56.25%;
  overflow: hidden;
}

.embed-container iframe,
.embed-container object,
.embed-container embed {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}
</style>
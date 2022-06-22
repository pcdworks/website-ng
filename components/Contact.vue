<template>
  <iframe
    onload="this.height=this.contentWindow.document.body.scrollHeight;"
    src=""
    class="contact"
  >
  </iframe>
</template>

<script>
export default {
  name: 'Contact',
  data: () => ({}),
}
</script>

<style lang="scss" scoped>
.contact {
  border: none;
  width: 100%;
  height: 200vh;
}
</style>
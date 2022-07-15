<template>
  <iframe
    onload="this.height=this.contentWindow.document.body.scrollHeight;"
    src="https://forms.monday.com/forms/embed/7e4bb1a9fe3134060f975cb2e3785e82?r=use1"
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
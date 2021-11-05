<template>
  <div></div>
</template>

<script>
export default {
  props: {
    name: {
      type: String,
      default: '',
    },
    title: {
      type: String,
      default: '',
    },
    education: {
      type: String,
      default: '',
    },
    avatar: {
      type: String,
      default: '/images/pcd-simple-512.png',
    },
  },
  data: () => {
  }
}
</script>

<style>

</style>
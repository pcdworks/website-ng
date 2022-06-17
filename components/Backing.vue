<template>
    <div class="backing">
        <slot></slot>
    </div>
</template>

<script>
export default {
    name: 'Backing',
    async asyncData ({ $content }) {
    const page = await $content('home').fetch()

    return {
      page
    }
  }
}
</script>

<style lang="scss" scoped>
@import '~vuetify/src/styles/settings/_variables';
.backing {
  padding-top: 48px;
  padding-bottom: 64px;
  min-height: 400px;
  background: #5e6e65;
  color: white;
}

</style>
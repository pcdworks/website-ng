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

<style scoped>

.backing {
  padding-top: 48px;
  min-height: 400px;
  background: #5e6e65;
}

</style>
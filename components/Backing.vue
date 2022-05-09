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

h1{
    font-size:5rem;
}

h2 {
  font-size: 3rem;
}

@media #{map-get($display-breakpoints, 'md-and-down')} {
  h1{
    font-size:2rem;
  }

  h2 {
    font-size: 1.5rem;
  }
}

</style>
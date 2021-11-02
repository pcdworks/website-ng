<template>
    <nuxt-content :document="doc" />
</template>

<script>
export default {
async asyncData({ $content, params }) {
  const doc = await $content(params.slug || params.pathMatch || 'home').fetch()
  return { doc }
},
head() {
  return {
    title: this.doc.title,
    script: [{ src: 'https://identity.netlify.com/v1/netlify-identity-widget.js' }],
    meta: [
      {
        hid: "description",
        name: "description",
        content: this.doc.description,
      },
      {
        hid: "og:title",
        name: "og:title",
        content: this.doc.title,
      },
      {
        hid: "og:description",
        name: "og:description",
        content: this.doc.description,
      },
    ]
    }
  }
}
</script>
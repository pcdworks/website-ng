<template>
    <div>
        <h1>Page not found</h1>
        <h2>The page you're looking for does not seem to exist</h2>
        <a href="/index">Go to Homepage</a>
    </div>
</template>

<script>
export default {
data () {
  return {
    doc: {
      description: 'The page you\'re looking for does not seem to exist',
      title: 'Page not found'
    }
  }
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
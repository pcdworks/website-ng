<template>
  <v-footer dark padless>
    <v-card flat tile class="secondary lighten-1 white--text text-center foot">
      <v-card-text>
        <template v-for="social in socials">
          <v-btn
            v-if="isLocal(social.link)"
            :key="social.icon"
            class="mx-2 mx-md-4 white--text"
            icon
            :to="social.link"
          >
            <v-icon size="24px">
              {{ social.icon }}
            </v-icon>
          </v-btn>
          <v-btn
            v-else
            :key="social.icon"
            class="mx-4 white--text"
            icon
            :href="social.link"
            target="_blank"
          >
            <v-icon size="24px">
              {{ social.icon }}
            </v-icon>
          </v-btn>
        </template>
      </v-card-text>

      <v-divider></v-divider>

      <v-card-text class="white--text">
        © {{ new Date().getFullYear() }} —
        <strong>Product Concept Development, Inc.</strong>
      </v-card-text>
    </v-card>
  </v-footer>
</template>

<script>
export default {
  name: 'Footer',
  data() {
    return {
      socials: [
        {
          icon: 'mdi-linkedin',
          link: 'https://www.linkedin.com/company/product-concept-development-inc-',
        },
        {
          icon: 'mdi-facebook',
          link: 'https://www.facebook.com/PCDworks/',
        },
        {
          icon: 'mdi-email',
          link: '/contact',
        },
        {
          icon: 'mdi-phone',
          link: 'tel:+19035492056',
        },
        {
          icon: 'mdi-google-maps',
          link: 'https://www.google.com/maps/place/Product+Concept+Development,+Inc./@31.971421,-95.6108545,15z/data=!4m5!3m4!1s0x0:0x98df75762eca2dd4!8m2!3d31.971421!4d-95.6108545',
        },
      ],
    }
  },
  methods: {
    isLocal(link) {
      if (link && link[0] === '/') {
        return true
      } else {
        return false
      }
    },
  },
}
</script>

<style lang="scss" scoped>
.foot {
  width: 100%;
}
</style>
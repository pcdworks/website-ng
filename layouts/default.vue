<template>
  <v-app dark>
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant="miniVariant"
      :clipped="true"
      fixed
      app
    >
      <v-list>
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
          :to="item.path"
          router
          exact
        >
          <v-list-item-action>
            <!-- <v-icon>{{ item.icon }}</v-icon> -->
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="item.nav_name" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar
      :clipped-left="true"
      fixed
      app
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <!-- <v-btn
        icon
        @click.stop="miniVariant = !miniVariant"
      >
        <v-icon>mdi-{{ `chevron-${miniVariant ? 'right' : 'left'}` }}</v-icon>
      </v-btn> -->
      <v-toolbar-title>
        <router-link to="/">
          <div class="logo">
            <img src="@/static/images/logo.png" alt="PCDworks logo" />
          </div>
        </router-link>
      </v-toolbar-title>
      <v-spacer />
    </v-app-bar>
    <v-main>
      <v-container>
        {{items}}
        <Nuxt />
      </v-container>
    </v-main>
    <v-footer absolute inset app>
      <span>&copy; 1997-{{ new Date().getFullYear() }} - Product Concept Development, Inc. - All Rights Reserved.</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data () {
    return {
      drawer: null,
      miniVariant: false,
      items: []
    }
  },
  async fetch() {
    this.items =  await this.$content('', { deep: true }).only(['nav_name']).fetch()
  }
}
</script>

<style>
.logo img {
  padding-top: 2px;
  padding-bottom: 2px;
  width: 310px;
  max-width: 100%;
}
.logo {
  width: 340px;
  max-width: 100%;
  margin: auto;
}
.v-toolbar__title {
  width: 100%;
  padding-right: 56px;
}
</style>
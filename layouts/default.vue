<template>
  <v-app>
    <v-navigation-drawer
      v-model="drawer"
      :clipped="true"
      fixed
      app
    >
      <v-list>
        <v-list-item
          v-for="(item, i) in topMenu"
          :key="i"
          :to="item.path"
          exact
        >
          <v-list-item-content>
            <v-list-item-title v-text="item.nav_name" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
      <v-list-group v-for="(group, name) in menu" :key="group.key">
        <template #activator>
          <v-list-item-title>{{name}}</v-list-item-title>
        </template>
        <v-list>
          <v-list-item
            v-for="(sitem, j) in group"
            :key="j"
            :to="sitem.path"
            exact
          >
            <v-list-item-content>
              <v-list-item-title v-text="sitem.nav_name" />
            </v-list-item-content>
          </v-list-item>
        </v-list>
      </v-list-group>

    </v-navigation-drawer>
    <v-app-bar
      :clipped-left="true"
      fixed
      app
    >
      <v-app-bar-nav-icon id="navi" @click.stop="drawer = !drawer">
        <v-icon>mdi-menu</v-icon>
        Menu
      </v-app-bar-nav-icon>
      <v-toolbar-title>
        <router-link to="/">
          <div class="logo">
            <img src="@/static/images/logo.png" alt="PCDworks logo" max-width="500px"/>
          </div>
        </router-link>
      </v-toolbar-title>
      <v-spacer />
      <v-btn icon @click="toggleDarkMode">
        <v-icon>{{switchIcon}}</v-icon>
      </v-btn>
    </v-app-bar>
    <v-main>
      <v-container>
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
      drawer: false,
      menu: [],
      topMenu: [],
      darkMode: false
    }
  },
  async fetch() {
    const items =  await this.$content('', { deep: true }).only(['nav_name', 'order', 'path']).fetch()
    for (const i in items.sort((a, b) => (a.order > b.order) ? 1 : -1)) {
      if(items[i].nav_name !== '') {
        this.setCategory(items[i])
      } else {
        delete items[i]
      }
    }
    this.menu = this.buildMenu(items)
    this.topMenu = this.menu.Top
    delete this.menu.Top
  },
  computed: {
    switchIcon () {
      return this.darkMode ? 'mdi-white-balance-sunny' : 'mdi-moon-waning-crescent';
    }
  },
  mounted () {
    const theme = localStorage.getItem("dark_theme");
    if (theme) {
        if (theme === "true") {
            this.$vuetify.theme.dark = true
            this.darkMode = true
        } else {
            this.$vuetify.theme.dark = false
            this.darkMode = false
        }
    } else if (
        window.matchMedia &&
        window.matchMedia("(prefers-color-scheme: dark)").matches
    ) {
        this.$vuetify.theme.dark = true
        this.darkMode = true
        localStorage.setItem(
            "dark_theme",
            this.$vuetify.theme.dark.toString()
        )
    }
  },
  methods: {
    toggleDarkMode () {
        this.$vuetify.theme.dark = !this.$vuetify.theme.dark;
        this.darkMode = !this.darkMode;
        localStorage.setItem(
            "dark_theme",
            this.$vuetify.theme.dark.toString()
        )
    },
    toTitleCase (str) {
      return str.replace(
        /\w\S*/g,
        function(txt) {
          return (txt.charAt(0).toUpperCase() + txt.substr(1).toLowerCase())
        }
      ).replace(/-/g, ' ')
    },
    setCategory (item) {
      if(item.path) {
        const path = item.path.split('/')
        if(path.length > 2) {
          item.category = this.toTitleCase(path[1])
        } else {
          item.category = 'Top'
        }
      }
    },
    buildMenu (items) {
      const groups = items.reduce((groups, item) => ({
        ...groups,
        [item.category]: [...(groups[item.category] || []), item]
      }), {})
      return groups
    }
  }
}
</script>

<style>

#navi {
  width: 64px;
  margin-left: 0px;
  margin-right: -12px;
}

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
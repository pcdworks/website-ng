<template>
  <v-app>
    <v-toolbar app>
    </v-toolbar>
    <v-main>
      <v-container fluid>
        <Nuxt />
      </v-container>
    </v-main>
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
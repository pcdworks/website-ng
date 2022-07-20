<template>
  <v-app>
    <v-app-bar app fixed hide-on-scroll elevation="2" height="100px" :color="bg" dark>
      <v-app-bar-nav-icon class="d-none d-flex d-sm-flex d-md-none"
                         aria-label="Menu" @click.stop="drawer = !drawer">
      </v-app-bar-nav-icon>
        <v-toolbar-title>
          <router-link to="/" alt="Home page">
            <Logo/>
          </router-link>
        </v-toolbar-title>
        &nbsp;&nbsp;
        <v-spacer class="d-none d-sm-none d-md-flex"></v-spacer>
        <v-btn text tile :class="navBtn" to="/">
          Home
        </v-btn>
        <!-- <div id="menu" class="d-none d-sm-none d-md-flex">
          <v-menu offset-y>
            <template #activator="{ on, attrs }">
              <v-btn text tile :class="navBtn" v-bind="attrs" v-on="on">
                Services
              </v-btn>
            </template>
            <v-list>
              <v-list-item
                v-for="(item, index) in menu.Services"
                :key="index"
                :to="item.path"
              >
                <v-list-item-title>{{ item.nav_name }}</v-list-item-title>
              </v-list-item>
            </v-list>
          </v-menu>
        </div> -->
        <v-btn v-for="item in topMenu" :key="item.nav_name" text tile :class="navBtn" :to="item.path">
          {{item.nav_name}}
        </v-btn>
      </v-app-bar>
    <v-navigation-drawer
      v-model="drawer"
      app
      temporary
    >
      <v-list
        nav
      >
        <v-list-item to="/">
          <v-list-item-title>
            Home
          </v-list-item-title>
        </v-list-item>
        <!-- <v-list-group>
          <template #activator>
            <v-list-item-content>
              <v-list-item-title v-text="'Services'"></v-list-item-title>
            </v-list-item-content>
          </template>
          <v-list-item
            v-for="(item, index) in menu.Services"
            :key="index"
            :to="item.path"
          >
            <v-list-item-title v-text="item.nav_name"></v-list-item-title>
          </v-list-item>
        </v-list-group> -->
        <v-list-item v-for="item in topMenu" :key="item.nav_name" :to="item.path">
          <v-list-item-title v-text="item.nav_name"></v-list-item-title>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-main :style="mainStyle">
      <v-container id="heart" fluid>
        <Nuxt />
          <v-btn fab dark large color="primary" fixed right bottom to="/contact" class="mb-md-4 mr-md-2 mr-0 mb-0">
              <v-icon v-if="$route.path === '/contact'" dark>mdi-email-edit</v-icon>
              <v-icon v-else dark>mdi-email</v-icon>
          </v-btn>
        <Footer />
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import Footer from '~/components/Footer.vue'
export default {
  components: { Footer },
  data () {
    return {
      drawer: false,
      menu: [],
      topMenu: [],
      darkMode: false,
      services: [],
      bg: '#212121',
      transparent: '#000000B3'
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
    },
    mainStyle() {
      if (this.$route.path === '/') {
        return 'padding-top: 0px;'
      }
      return 'padding-top: 100px;'
    },
    navBtn() {
      let classValue = 'd-none d-sm-none d-md-flex nav-btn'
      if (this.bg === this.transparent) {
        classValue += ' white--text'
      }
      return classValue
    }
  },
  watch: {
    $route(to, from) {
        this.changeColor()
    }
  },
  mounted () {
    window.onscroll = () => {
      this.changeColor()
    }
    this.changeColor()
  },
  methods: {
    changeColor() {
      if (
        document.body.scrollTop > 100 ||
        document.documentElement.scrollTop > 100 ||
        this.$route.path !== '/'
      ) {
        this.bg = '#212121'
      } else {
        this.bg = this.transparent
      }
    },
    darkModeInit () {
      const theme = localStorage.getItem("dark_theme")
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
      if(item.path && item.path !== '/index' && item.path !== '/expertise' && item.path !== '/campus' && item.path !== '/contact') {
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
  },
}
</script>

<style lang="scss">

primary,
primary h1,
primary h2,
primary h3,
primary h4,
primary p,
primary ul {
  color: #afbd21 !important;
}

secondary,
secondary h1,
secondary h2,
secondary h3,
secondary h4,
secondary p,
secondary ul {
  color: #5E6E65 !important;
}

black,
black h1,
black h2,
black h3,
black h4,
black p,
black ul {
  color: #000000 !important;
}

right {
  text-align: right;
}

#heart {
  padding: 0 !important;
}

.nuxt-content {
  margin-bottom: -6.2px !important;
}

.v-toolbar__content, .v-toolbar__extension {
  padding-left: 32px;
  padding-right: 32px;
}

.nav-btn {
  font-size: 1rem !important;
  font-weight: 700;
}

#menu {
  margin: 0 auto;
}

h1 {
  text-transform: uppercase;
  font-size:5rem;
}

h2 {
  font-size: 3rem;
}

h3 {
  font-size: 2rem;
}

h4 {
  font-size: 1.6rem;
}

p,
ul {
  font-size: 1.3rem;
}

@media #{map-get($display-breakpoints, 'md-and-down')} {

  h1{
    font-size:3rem;
  }

  h2 {
    font-size: 2rem;
  }

  h3 {
    font-size: 1.5rem;
  }

  h4 {
    font-size: 1.3rem;
  }

  p,
  ul {
    font-size: 1rem;
  }

}

</style>

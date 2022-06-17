<template>
  <v-app>
    <v-app-bar app fixed hide-on-scroll elevation="2" height="100px" color="white" light>
      <v-app-bar-nav-icon class="d-none d-flex d-sm-flex d-md-none"
                         aria-label="Menu" @click.stop="drawer = !drawer">
      </v-app-bar-nav-icon>
      <v-row align="center" align-content="center">
        <v-col cols="12" xl="3" lg="3" md="2" sm="12" xs="12">
          <center>
            <v-toolbar-title>
              <router-link to="/" alt="Home page">
                <Logo/>
              </router-link>
            </v-toolbar-title>
          </center>
        </v-col>
        <v-col cols="6" lg="6" md="8" class="d-none d-sm-none d-md-flex" xl="6" align-self="center">
          <div id="menu">
          <v-menu offset-y>
            <template #activator="{ on, attrs }">
              <v-btn text tile class="nav-btn" v-bind="attrs" v-on="on">
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
          <v-btn v-for="item in topMenu" :key="item.nav_name" text tile class="nav-btn" :to="item.path">
            {{item.nav_name}}
          </v-btn>
          </div>
        </v-col>
        <v-col cols="3" lg="3" md="2" class="d-none d-sm-none d-md-flex" align-self="center" xl="3">
          <a id="contact-btn" class="nav-btn" href="#contact">
            <span>Contact</span>
          </a>
        </v-col>
      </v-row>
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
        <v-list-group>
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
        </v-list-group>
        <v-list-item v-for="item in topMenu" :key="item.nav_name" :to="item.path">
          <v-list-item-title v-text="item.nav_name"></v-list-item-title>
        </v-list-item>
        <v-list-item href="#contact">
          <v-list-item-title>
            Contact
          </v-list-item-title>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-main>
      <v-container id="heart" fluid>
        <Nuxt />
        <contact-form/>
        <div id="because-i-have-to"></div>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import ContactForm from '~/components/ContactForm.vue'
export default {
  components: { ContactForm },
  data () {
    return {
      drawer: false,
      menu: [],
      topMenu: [],
      darkMode: false,
      services: []
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
  },
  methods: {
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
      if(item.path && item.path !== '/index') {
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

<style lang="scss">

iframe {
  height: auto;
  width: 100%;
  aspect-ratio: 21 / 9;
  padding: 3em;
}

.learn-more {
  background: #afbd21;
  text-align: center;
  text-decoration: none;
  border: 0;
  outline: 0;
  padding: 12px 44px;
  display: inline-block;
  transform: skew(-30deg);
  text-transform: uppercase;
  margin: 0 auto;
  max-width: 100%;
  color: black;
  text-transform: uppercase;
  font-weight: 680;
}

.learn-more:visited {
  color: black;
}

.learn-more > span {
  display: inline-block;
  transform: skew(30deg);
  color: black;
}

#heart {
  padding: 0 !important;
}

.v-toolbar__content, .v-toolbar__extension {
  padding-left: 32px;
  padding-right: 32px;
}

.nav-btn {
  font-size: 1rem !important;
  font-weight: 700;
  color: black !important;
}

#contact-btn {
  background: #afbd21;
  text-align: center;
  text-decoration: none;
  border: 0;
  outline: 0;
  padding: 12px 24px;
  display: inline-block;
  transform: skew(-30deg);
  text-transform: uppercase;
  margin: 0 auto;
  max-width: 100%;
}

#contact-btn-pad {
  -webkit-box-sizing: border-box; /* Safari/Chrome, other WebKit */
  -moz-box-sizing: border-box;    /* Firefox, other Gecko */
  box-sizing: border-box;         /* Opera/IE 8+ */
  max-width: 312px;
  width: 100%;
  text-align: center;
}

#contact-btn:visited {
  color: #fff;
}

#contact-btn > span {
  display: inline-block;
  transform: skew(30deg);
}

#menu {
  margin: 0 auto;
}

#because-i-have-to {
  height: 128px;
  background: #5E6E65;
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

p,
ul {
  font-size: 1.5rem;
}

@media #{map-get($display-breakpoints, 'md-and-down')} {

  iframe {
    height: auto;
    width: 100%;
    aspect-ratio: 9 / 16;
    padding: 1em;
  }

  h1{
    font-size:3rem;
  }

  h2 {
    font-size: 2rem;
  }

  h3 {
    font-size: 1.5rem;
  }

  p,
  ul {
    font-size: 1rem;
  }

}

</style>
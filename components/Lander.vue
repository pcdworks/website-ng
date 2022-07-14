<template>
  <v-img :src="getImage" :aspect-ratio="getAspect" :gradient="getFilter">
    <v-row class="py-16 lander fill-height" align="center">
      <v-col align-self="center">
        <div v-if="hasBacking" class="mt-16 panel py-4 px-2 mr-4 px-md-10 px-lg-16" :style="'background: ' + backing">
          <center v-if="getCenter">
            <slot></slot>
          </center>
          <slot v-else></slot>
        </div>
        <div v-else class="px-xl-16 px-lg-16 px-md-4 px-xs-0 mx-1">
          <div class="mt-16 mx-4 mx-md-8 mx-lg-16">
            <center v-if="getCenter">
              <slot></slot>
            </center>
            <slot v-else></slot>
          </div>
        </div>
        <div class="px-xl-16 px-lg-16 px-md-4 px-xs-0 mx-1">
          <v-row class="px-xl-16 px-lg-16 px-md-4 px-xs-0 mx-2">
            <v-col
              v-for="(card, idx) in getCards"
              :key="idx"
              cols="12"
              xs="12"
              sm="12"
              md="12"
              xl="4"
              lg="4"
            >
              <v-card
                elevation="8"
                class="pb-6 fill-height d-flex flex-column"
                tile
              >
                <v-card-title v-if="card.top_title">
                  <div class="top-title">
                    <center>{{ card.title }}</center>
                  </div>
                </v-card-title>
                <div v-else class="pt-6"></div>
                <br />
                <center>
                  <v-img
                    :src="card.image"
                    max-width="160"
                    max-height="160"
                    :alt="card.title"
                    contain
                  ></v-img>
                </center>
                <v-card-subtitle v-if="!card.top_title">
                  <div
                    class="
                      px-xl-16 px-lg-4 px-md-12 px-sm-10 px-xs-4
                      entry-title
                    "
                  >
                    <center>{{ card.title }}</center>
                  </div>
                </v-card-subtitle>
                <v-card-text>
                  <p
                    class="
                      entry-text
                      px-xl-16 px-lg-4 px-md-12 px-sm-10 px-xs-4
                    "
                  >
                    <center>{{ card.text }}</center>
                  </p>
                </v-card-text>
                <v-spacer />
                <v-card-actions>
                  <v-row align="center">
                    <v-spacer/>
                    <v-tooltip top>
                      <template #activator="{ on, attrs }">
                      <v-btn
                        x-large
                        color="primary"
                        :to="card.link"
                        :aria-label="card.title"
                        :alt="card.title"
                        v-bind="attrs"
                        v-on="on">
                          Learn More
                        </v-btn>
                      </template>
                      <span>Learn More About {{ card.title }}</span>
                    </v-tooltip>
                    <v-spacer/>
                  </v-row>
                </v-card-actions>
              </v-card>
            </v-col>
          </v-row>
        </div>
      </v-col>
    </v-row>
    <div v-if="snow">
      <div class="snowflakes" aria-hidden="true">
        <div class="snowflake">❅</div>
        <div class="snowflake">❆</div>
        <div class="snowflake">❅</div>
        <div class="snowflake">❆</div>
        <div class="snowflake">❅</div>
        <div class="snowflake">❆</div>
        <div class="snowflake">❅</div>
        <div class="snowflake">❆</div>
        <div class="snowflake">❅</div>
        <div class="snowflake">❆</div>
        <div class="snowflake">❅</div>
        <div class="snowflake">❆</div>
      </div>
    </div>
  </v-img>
</template>

<script>
export default {
  name: 'Lander',
  props: {
    content: {
      type: Object,
      default: () => {
        return {
          filter: '',
          image: '',
          center: false
        }
      },
    },
    snow: {
      type: Boolean,
      default: false,
    },
    backing: {
      type: String,
      default: ''
    },
    image: {
      type: String,
      default: ''
    },
    center: {
      type: Boolean,
      default: false
    },
    filter: {
      type: String,
      default: ''
    },
    cards: {
      type: Array,
      default: () => []
    }
  },
  computed: {
    getAspect() {
      if(this.image === '' && this.content.image === '') {
        return 0
      }
      return 18 / 9
    },
    getCenter() {
      return this.center || this.content.center
    },
    getFilter() {
      if (this.filter !== '') {
        return this.filter
      } else {
        return this.content.filter
      }
    },
    getCards() {
      if (this.cards && this.cards.length !== 0) {
        return this.cards
      } else {
        return this.content.cards
      }
    },
    getImage() {
      if(this.image !== '') {
        return this.image
      } else {
        return this.content.image
      }
    },
    hasBacking() {
      return this.backing !== ''
    }
  }
}
</script>

<style lang="scss" scoped>
.panel {
  display: inline-block;
  border-top-right-radius: 8px;
  border-bottom-right-radius: 8px;    
}

.top-title {
  background: #5e6e64;
  width: 100%;
  color: white;
  text-transform: uppercase;
  font-size: 2rem;
  line-height: 3rem;
  height: 3rem;
  font-weight: 650;
  white-space: normal;
  word-break: break-word;
}

.entry-title {
  color: #afbd21;
  font-size: 1.75rem;
  font-weight: 750;
  line-height: 1.85rem;
  text-transform: uppercase;
}

.entry-text {
  color: #5e6e64;
  font-weight: 600;
}

::v-deep h1,
::v-deep h2,
::v-deep h3,
::v-deep p,
::v-deep ul,
::v-deep a {
  color: rgba(255, 255, 255, 1);
}

@media #{map-get($display-breakpoints, 'lg-only')} {
  .top-title {
    font-size: 1.1rem;
    height: 1.6rem;
    line-height: 1.6rem;
  }
}

@media #{map-get($display-breakpoints, 'md-and-down')} {
  .top-title {
    font-size: 1rem;
    height: 1.5rem;
    line-height: 1.5rem;
  }
}

/* snow thanks to https://github.com/pajasevi/CSSnowflakes */
.snowflake {
  color: #fff;
  font-size: 0.7em;
  font-family: Arial, sans-serif;
  text-shadow: 0 0 5px #555;
}

@-webkit-keyframes snowflakes-fall {
  0% {
    top: -10%;
  }

  100% {
    top: 100%;
  }
}

@-webkit-keyframes snowflakes-shake {
  0% {
    -webkit-transform: translateX(0px);
    transform: translateX(0px);
  }

  50% {
    -webkit-transform: translateX(80px);
    transform: translateX(80px);
  }

  100% {
    -webkit-transform: translateX(0px);
    transform: translateX(0px);
  }
}

@keyframes snowflakes-fall {
  0% {
    top: -10%;
  }

  100% {
    top: 100%;
  }
}

@keyframes snowflakes-shake {
  0% {
    transform: translateX(0px);
  }

  50% {
    transform: translateX(80px);
  }

  100% {
    transform: translateX(0px);
  }
}

.snowflake {
  position: fixed;
  top: -10%;
  z-index: 9999;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
  cursor: default;

  -webkit-animation-name: snowflakes-fall, snowflakes-shake;
  -webkit-animation-duration: 10s, 3s;
  -webkit-animation-timing-function: linear, ease-in-out;
  -webkit-animation-iteration-count: infinite, infinite;
  -webkit-animation-play-state: running, running;

  animation-name: snowflakes-fall, snowflakes-shake;
  animation-duration: 10s, 3s;
  animation-timing-function: linear, ease-in-out;
  animation-iteration-count: infinite, infinite;
  animation-play-state: running, running;
}
.snowflake:nth-of-type(0) {
  left: 1%;
  -webkit-animation-delay: 0s, 0s;
  animation-delay: 0s, 0s;
}
.snowflake:nth-of-type(1) {
  left: 10%;
  -webkit-animation-delay: 1s, 1s;
  animation-delay: 1s, 1s;
}
.snowflake:nth-of-type(2) {
  left: 20%;
  -webkit-animation-delay: 6s, 0.5s;
  animation-delay: 6s, 0.5s;
}
.snowflake:nth-of-type(3) {
  left: 30%;
  -webkit-animation-delay: 4s, 2s;
  animation-delay: 4s, 2s;
}
.snowflake:nth-of-type(4) {
  left: 40%;
  -webkit-animation-delay: 2s, 2s;
  animation-delay: 2s, 2s;
}
.snowflake:nth-of-type(5) {
  left: 50%;
  -webkit-animation-delay: 8s, 3s;
  animation-delay: 8s, 3s;
}
.snowflake:nth-of-type(6) {
  left: 60%;
  -webkit-animation-delay: 6s, 2s;
  animation-delay: 6s, 2s;
}
.snowflake:nth-of-type(7) {
  left: 70%;
  -webkit-animation-delay: 2.5s, 1s;
  animation-delay: 2.5s, 1s;
}
.snowflake:nth-of-type(8) {
  left: 80%;
  -webkit-animation-delay: 1s, 0s;
  animation-delay: 1s, 0s;
}
.snowflake:nth-of-type(9) {
  left: 90%;
  -webkit-animation-delay: 3s, 1.5s;
  animation-delay: 3s, 1.5s;
}
.snowflake:nth-of-type(10) {
  left: 25%;
  -webkit-animation-delay: 2s, 0s;
  animation-delay: 2s, 0s;
}
.snowflake:nth-of-type(11) {
  left: 65%;
  -webkit-animation-delay: 4s, 2.5s;
  animation-delay: 4s, 2.5s;
}
</style>
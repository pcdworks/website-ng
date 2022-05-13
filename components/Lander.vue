<template>
  <v-img :src="content.image" :aspect-ratio="16/9"
         :gradient="content.filter">
    <v-row class="py-16 lander fill-height">
      <v-col align="center">
        <div class="px-xl-16 px-lg-16 px-md-4 px-xs-0 mx-1">
          <!-- eslint-disable vue/no-v-html -->
          <h1 v-html="content.title"></h1>
          <!--eslint-enable-->
          <p>{{content.subtitle}}</p>
          <br>
          <v-row class="px-xl-16 px-lg-16 px-md-4 px-xs-0 mx-2">
            <v-col v-for="(card, idx) in content.cards" :key="idx"
                  cols="12" xs="12" sm="12" md="12" xl="4" lg="4">
              <v-card elevation="8" class="pb-6 fill-height person" tile>
                <v-card-title v-if="card.top_title">
                  <div class="top-title">{{card.title}}</div>
                </v-card-title>
                <div v-else class="pt-6"></div>
                  <br/>
                  <v-img
                      :src="card.image"
                      max-width="160"
                      max-height="160"
                      contain></v-img>
                  <v-card-subtitle v-if="!card.top_title">
                      <div class="px-xl-16 px-lg-4 px-md-12 px-sm-10 px-xs-4 entry-title">
                        {{card.title}}
                      </div>
                  </v-card-subtitle>
                  <v-card-text>
                      <p class="entry-text px-xl-16 px-lg-4 px-md-12 px-sm-10 px-xs-4">
                        {{card.text}}
                      </p>
                  </v-card-text>
                  <v-card-actions>
                    <a class="learn-more" :href="card.link">
                      <span>Learn More</span>
                    </a>
                  </v-card-actions>
              </v-card>
            </v-col>
          </v-row>
        </div>
      </v-col>
    </v-row>
  </v-img>
</template>

<script>
export default {
    name: 'Lander',
    props: {
      content: {
          type: Object,
          default: () => {}
      }
    }
}
</script>

<style lang="scss" scoped>

.top-title {
  background: #5e6e64;
  width: 100%;
  color: white;
  text-transform: uppercase;
  font-size: 2rem;
  height: 3rem;
  line-height: 3rem;
  font-weight: 650;
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
  font-size: 1.2rem;
}

h1{
    font-size:5rem;
    color: rgba(255, 255, 255, 1);
}

h2 {
  font-size: 3rem;
  color: rgba(255, 255, 255, 1);;
}

p {
  font-size: 1.5rem;
  color: rgba(255, 255, 255, 1);;
  max-width: 50rem;
  font-weight: 650;
}


@media #{map-get($display-breakpoints, 'md-and-down')} {
  h1{
    font-size:2.5rem;
    color: rgba(255, 255, 255, 1);;
  }
}

</style>
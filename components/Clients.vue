<template>
    <v-row class="py-16">
        <v-col align="center" cols="12">
            <div class="px-xl-16 px-lg-16 px-md-4 px-xs-0 mx-1">
                <slot></slot>
            </div>
        </v-col>
        <v-col cols="12">
            <v-row class="py-4 px-16" align="justify">
                <v-col v-for="(logo, idx) in logos" :key="idx"
                    cols="12" lx="2" lg="2" md="3" sm="4">
                    <v-list-item :href="logo.link" target="_blank">
                        <v-img :src="logo.image" :alt="logo.alt" contain></v-img>
                    </v-list-item>
                </v-col>
            </v-row>
        </v-col>
    </v-row>
</template>

<script>
export default {
    name: 'Clients',
    props: {
      logos: {
          type: Array,
          default: () => []
      }
    }
}
</script>

<style lang="scss" scoped>

::v-deep h1{
    font-size:5rem;
    color: #5e6e64;
    line-height: normal;
}

::v-deep h2 {
  font-size: 3rem;
  color: #5e6e64;
}

::v-deep p {
  font-size: 1.5rem;
  color: #5e6e64;
  max-width: 50rem;
  font-weight: 650;
}

@media #{map-get($display-breakpoints, 'md-and-down')} {
  h1{
    font-size:2.2rem;
    line-height: normal;
  }

  h2{
      font-size: 1.2rem;
  }
}

</style>
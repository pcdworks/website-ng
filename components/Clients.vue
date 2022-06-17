<template>
    <div class="backing">
        <v-row class="py-16" align="center">
            <v-col align-self="center" cols="12">
                <div class="px-xl-16 px-lg-16 px-md-4 px-xs-0 mx-1">
                    <center>
                        <slot></slot>
                    </center>
                </div>
            </v-col>
            <v-col cols="12" align-self="center">
                <v-row class="py-4 px-16" align="stretch">
                    <v-col v-for="(logo, idx) in logos" :key="idx"
                        cols="12" lx="2" lg="2" md="3" sm="4">
                        <v-list-item :href="logo.link" target="_blank">
                            <v-img :src="logo.image" :alt="logo.alt" contain></v-img>
                        </v-list-item>
                    </v-col>
                </v-row>
            </v-col>
        </v-row>
    </div>
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

.backing {
    position: relative;
    background: white;
}

::v-deep h1,
::v-deep h2,
::v-deep h3,
::v-deep p {
  color: #5e6e64;
}

</style>
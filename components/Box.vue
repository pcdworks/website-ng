<template>
    <v-img :src="background" :aspect-ratio="aspect" :gradient="filter">    
        <div class="px-xl-16 px-lg-16 px-md-4 px-xs-0 mx-1 py-16 fill-height">
            <v-row :id="color" class="px-xl-16 px-lg-16 px-md-4 px-xs-0 mx-2">
                <v-col cols="4" sm="2" md="2" ld="2">
                    <v-img v-if="hasImage" :src="image" contain aspect-ratio="1"></v-img>
                </v-col>
                <v-col align-self="center" cols="8" sm="10" md="10" lg="10">
                    <slot></slot>
                </v-col>
                <v-col cols="12">
                    <center>
                        <v-btn v-if="hasButton" :to="button.link" color="primary">
                            {{button.text}}
                        </v-btn>
                    </center>
                </v-col>
            </v-row>
        </div>
    </v-img>
</template>

<script>
export default {
    name: 'Box',
    props: {
        filter: {
            type: String,
            default: ''
        },
        background: {
            type: String,
            default: ''
        },
        image: {
            type: String,
            default: ''
        },
        aspect: {
            type: Number,
            default: 0
        },
        color: {
            type: String,
            default: 'white'
        },
        button: {
            type: Object,
            default: () => {}
        },
    },
    computed: {
        hasButton() {
            return this.button && Object.keys(this.button).length !== 0
        },
        hasImage() {
            return this.image !== ''
        }
    }
}
</script>

<style lang="scss" scoped>
::v-deep #white h1,
::v-deep #white h2,
::v-deep #white h3,
::v-deep #white p,
::v-deep #white ul,
::v-deep #white a {
  color: rgba(255, 255, 255, 1);
}

::v-deep #black h1,
::v-deep #black h2,
::v-deep #black h3,
::v-deep #black p,
::v-deep #black ul,
::v-deep #black a {
  color: rgba(0, 0, 0, 1);
}
</style>
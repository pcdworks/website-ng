<template>
    <div class="px-xl-16 px-lg-16 px-md-4 px-xs-0"
        :style="'background: ' + background">
        <div class="mx-md-8 mx-lg-16">
            <v-row class="py-16 fill-height" align="center">
                <v-col align-self="center" cols="12" class="pa-8 pa-md-16">
                    <h3><u><b>{{title}}</b></u></h3>
                    <center v-if="center">
                        <slot></slot>
                    </center>
                    <slot v-else></slot>
                </v-col>
                <v-col cols="12" md="6" class="pa-8 pl-md-16">
                    <slot name="secondary"></slot>
                    <br/>
                    <v-btn v-if="hasButton" :href="button.link" color="primary" target="_blank">{{button.text}}</v-btn>
                </v-col>
                <v-col cols="12" md="6" class="pa-8 pr-md-16">
                    <slot name="tertiary"></slot>
                </v-col>
            </v-row>
        </div>
    </div>
</template>

<script>
export default {
    name: 'TriForce',
    props: {
        center: {
            type: Boolean,
            default: false
        },
        background: {
            type: String,
            default: '#1f1f1f'
        },
        button: {
            type: Object,
            default: () => {}
        },
        title: {
            type: String,
            default: ''
        },
    },
    computed: {
        hasButton() {
            return this.button && Object.keys(this.button).length !== 0
        }
    }
}
</script>

<style lang="scss" scoped>
::v-deep h1,
::v-deep h2,
::v-deep h3,
::v-deep h4,
::v-deep p,
::v-deep ul,
::v-deep a {
  color: rgba(255, 255, 255, 1);
}

</style>
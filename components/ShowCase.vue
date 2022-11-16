<template>
    <v-img :src="background" :aspect-ratio="aspect" :gradient="filter">
        <div class="px-md-8 mx-md-4 px-lg-16 mx-lg-16">
            <v-row class="ma-4 pa-4 pa-md-8 ma-md-16" align="center">
                <v-col cols="12" align-self="center">
                    <div :id="color">
                        <center v-if="center">
                            <slot></slot>
                        </center>
                        <slot v-else></slot>
                    </div>
                </v-col>
            </v-row>
            <v-card class="ma-4 pa-4 pa-md-8 ma-md-16">
                <v-row class="">
                    <v-col v-for="(panel, key) in panels" :key="key" cols="12" md="3">
                        <v-hover v-slot="{ hover }" transition="slide-x-transition">
                            <v-card class="my-0">
                                <v-img :aspect-ratio="1" :src="panel.image" max-height="300px">
                                    <v-expand-transition>
                                        <v-card
                                            v-if="hover"
                                            class="
                                            fill-height d-flex flex-column
                                            primary
                                            transition-fast-in-fast-out
                                            v-card--reveal
                                            black--text
                                            "
                                            style="height: 100%;"
                                        >
                                            <v-card-title v-resize-text="{
                                                    ratio: 8,
                                                    minFontSize: '10px',
                                                    maxFontSize: '26px',
                                                    delay: 200,
                                                }"
                                                class="case-title d-flex d-sm-none">{{panel.title}}</v-card-title>
                                            <v-card-title v-resize-text="{
                                                    ratio: 8,
                                                    minFontSize: '12px',
                                                    maxFontSize: '26px',
                                                    delay: 200,
                                                }"
                                                class="case-title d-none d-sm-flex">{{panel.title}}</v-card-title>
                                            <v-card-text>
                                            <div
                                                v-resize-text="{
                                                    ratio: 3.5,
                                                    minFontSize: '12px',
                                                    maxFontSize: '26px',
                                                    delay: 200,
                                                }"
                                                class="px-2 py-0 my-0 case-body"
                                                >
                                                <span>{{panel.summary}}</span>
                                            </div>
                                            </v-card-text>
                                            <v-card-actions class="case-action">
                                                <v-btn :to="panel.link" outlined>Learn More</v-btn>
                                            </v-card-actions>
                                        </v-card>
                                    </v-expand-transition>
                                </v-img>
                            </v-card>
                        </v-hover>
                    </v-col>
                </v-row>
            </v-card>
        </div>
    </v-img>
</template>

<script>

export default {
    name: 'ShowCase',
    props: {
        panels: {
            type: Array,
            default: () => []
        },
        filter: {
            type: String,
            default: ''
        },
        background: {
            type: String,
            default: ''
        },
        aspect: {
            type: String,
            default: ''
        },
        center: {
            type: Boolean,
            default: false
        },
        color: {
            type: String,
            default: 'white'
        }
    },
    methods: {}
}
</script>

<style lang="scss" scoped>
.case-title {
    white-space: nowrap;
    word-break: break-word;
    text-overflow: ellipsis;
    height: 64px;
}

.case-body {
    height: 152px;
    display: -webkit-box;
    max-width: 100%;
    -webkit-line-clamp: 7;
    -webkit-box-orient: vertical;
    overflow: hidden;
    color: black;
    border: 1px solid black;
}

.case-action {
    height: 42px;
}

::v-deep #white h1,
::v-deep #white h2,
::v-deep #white h3,
::v-deep #white h4,
::v-deep #white p,
::v-deep #white ul,
::v-deep #white a {
  color: rgba(255, 255, 255, 1);
}

::v-deep #black h1,
::v-deep #black h2,
::v-deep #black h3,
::v-deep #black h4,
::v-deep #black p,
::v-deep #black ul,
::v-deep #black a {
  color: rgba(0, 0, 0, 1);
}
</style>
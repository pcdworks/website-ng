<template>
    <div class="px-xl-16 px-lg-16 px-md-4 px-xs-0">
        <div class="px-xl-16 px-lg-16 px-md-4 px-xs-0">
            <v-row>
                <v-col v-for="(work, idx) in works" :key="idx" cols="12" xl="6" ld="6" md="6">
                    <icon-header :image="work.image" :text="work.title"/>
                    <v-row v-for="(w, i) in work.works" :key="i">
                        <v-col>
                            <v-card elevation="0" class="pt-6 pb-6 fill-height" flat>
                                <v-card-title>
                                    <div class="work">{{w.title}}</div>
                                </v-card-title>
                                <v-card-text>
                                    <p v-if="w.subtitle"><strong>{{w.subtitle}}</strong></p>
                                    <p v-if="w.image && w.image != ''">
                                        <v-img :src="w.image" :aspect-ratio="16/9" contain></v-img>
                                    </p>
                                    <p v-if="w.problem">
                                        <strong>PROBLEM: </strong>{{w.problem}}
                                    </p>
                                    <p v-if="w.solution">
                                        <strong>SOLUTION: </strong>{{w.solution}}
                                    </p>
                                    <p v-if="w.results">
                                        <strong>RESULTS: </strong>{{w.results}}
                                    </p>
                                </v-card-text>
                            </v-card>
                        </v-col>
                    </v-row>
                </v-col>
            </v-row>
            <br/>
        </div>
    </div>
</template>

<script>
import IconHeader from './IconHeader.vue'
export default {
  name: 'WorkSplitVert',
  components: { IconHeader },
    props: {
        works: {
            type: Array,
            default: () => []
        }
    }
}
</script>

<style scoped>
.work {
    white-space: normal;
    word-break: break-word;
}
</style>
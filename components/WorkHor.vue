<template>
    <div class="pa-xl-16 pa-lg-16 pa-md-4 pa-xs-0">
        <div class="pa-xl-16 pa-lg-16 pa-md-4 pa-xs-0">
            <icon-header :image="work.image" :text="work.title"/>
            <v-row>
                <v-col v-for="(w, idx) in work.works" :key="idx" cols="12" xl="4" ld="4" md="4">
                    <v-card elevation="0" class="pt-6 pb-6 fill-height" flat>
                        <v-card-title>
                            {{w.title}}
                        </v-card-title>
                        <v-card-text>
                            <p v-if="w.subtitle"><strong>{{w.subtitle}}</strong></p>
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
        </div>
    </div>
</template>

<script>
import IconHeader from './IconHeader.vue'
export default {
  name: 'WorkHor',
  components: { IconHeader },
    props: {
        work: {
            type: Object,
            default: () => {}
        }
    }
}
</script>

<style scoped>

</style>
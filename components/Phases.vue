<template>
    <div class="pa-xl-16 pa-lg-16 pa-md-4 pa-xs-0">
        <v-row class="px-xl-16 px-lg-16 px-md-4 px-xs-0">
            <v-col v-for="p in phases" :key="p.name"
                   cols="12" xs="12" sm="12" md="12" xl= "4" lg="4">
                   <Phase :title="p.title"
                          :image="p.image"
                          :subtitle="p.subtitle"
                          :bullets="p.bullets">
                   </Phase>
            </v-col>
        </v-row>
    </div>
</template>


<script>
export default {
    name: 'Phases',
    props: {
        phases: {
            type: Array,
            default: () => []
        }
    }
}
</script>
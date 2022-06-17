<template>
    <div class="pa-xl-16 pa-lg-16 pa-md-4">
        <v-row class="px-xl-16 px-lg-16 px-md-4">
            <v-col v-for="p in people" :key="p.name"
                   cols="12" xs="12" sm="12" md="12" xl= "4" lg="4"
                   class="pa-0 mb-4">
                <Person
                    :name="p.name"
                    :degrees="p.degrees"
                    :position="p.position"
                    :image="p.image"
                    :bio="p.bio"
                    :phone="p.phone"
                    :email="p.email"
                    :linkedin="p.linkedin"
                    :twitter="p.twitter"
                    :website="p.website">
                </Person>
            </v-col>
        </v-row>
    </div>
</template>

<script>
export default {
    name: 'People',
    props: {
        people: {
            type: Array,
            default: () => []
        }
    }
}
</script>

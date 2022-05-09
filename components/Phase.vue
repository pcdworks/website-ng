<template>
    <v-card elevation="10" class="pt-6 pb-16 fill-height">
        <v-card-title>
            <v-img :src="image" max-height="150px" max-width="150px"></v-img>
            <div class="phase-title">{{title}}</div>
        </v-card-title>
        <v-card-subtitle>
            <div class="phase-subtitle">{{subtitle}}</div>
        </v-card-subtitle>
        <v-card-text>
            <ul class="phase-text">
                <div v-for="(item, idx) in bullets" :key="idx">
                    <li v-if="typeof(item) == 'string'">{{item}}</li>
                    <ul v-else>
                        <li v-for="(itm, ix) in item" :key="ix">
                            {{itm}}
                        </li>
                    </ul>
                </div>
            </ul>
        </v-card-text>
    </v-card>
</template>

<script>
export default {
    name: 'Phase',
    props: {
        image: {
            type: String,
            default: ''
        },
        title: {
            type: String,
            default: ''
        },
        subtitle: {
            type: String,
            default: ''
        },
        bullets: {
            type: Array,
            default: () => {}
        }
    }
}
</script>

<style lang="scss" scoped>
.phase-title {
    color: #afbc21;
    font-size: 2.8rem;
    font-weight: 600;
    padding-left: 2rem;
}

.phase-subtitle {
    padding-top: 3rem;
    color: black;
    font-size: 1.7rem;
    font-weight: 600;
}

.phase-text {
    color: #5e6e64;
    font-size: 1rem;
    font-weight: 600;
}
</style>
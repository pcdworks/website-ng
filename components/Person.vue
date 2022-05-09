<template>
    <v-card elevation="8" class="pt-6 pb-16 fill-height">
        <br/>
        <v-img
            lazy-src="/images/person.png"
            :src="image"
            transition
            width="254"
            height="254"
            contain
            class="person-image"></v-img>
        <v-card-subtitle>
            <div class="top-name">{{name}}, {{degrees}}</div><br>
            <div class="bottom-name">{{position}}</div>
        </v-card-subtitle>
        <v-card-text>
            <div class="bio pt-3 px-xl-16 px-lg-4 px-md-12 px-sm-10 px-xs-4">{{bio}}</div>
        </v-card-text>
    </v-card>
</template>

<script>
export default {
    name: 'Person',
    props: {
        image: {
            type: String,
            default: '/images/person.png'
        },
        name: {
            type: [String,Boolean],
            default: ''
        },
        degrees: {
            type: String,
            default: ''
        },
        position: {
            type: String,
            default: 'Human'
        },
        bio: {
            type: String,
            default: ''
        }
    }
}
</script>

<style scoped>
.person-image {
    border-radius: 50%;
    max-height: 254px;
    max-width: 254px;
    border: 2px #626363 solid;
    margin-bottom: 2.2rem;
}

.top-name {
    color: #afbc21;
    font-size: 1.75rem;
    font-weight: 750;
    line-height: 1.85rem;
}

.bottom-name {
    color: #afbc21;
    text-transform: uppercase;
    font-size: 2.2rem;
    font-weight: 700;
}

.bio {
    color: #839088;
    font-size: 1.5rem;
    font-weight: 520;
    line-height: 1.7rem;
}

</style>
<template>
    <v-card elevation="8" class="pt-6 fill-height person d-flex flex-column" tile>
        <br/>
        <center>
            <v-img
                lazy-src="/images/person.webp"
                :src="image"
                width="254"
                height="254"
                contain
                class="person-image"></v-img>
        </center>

        <v-card-subtitle>
            <div class="top-name">{{name}}, {{degrees}}</div><br>
            <div class="bottom-name">{{position}}</div>
        </v-card-subtitle>
        <v-card-text>
            <div class="bio pt-3 px-xl-16 px-lg-4 px-md-12 px-sm-10 px-xs-4">{{bio}}</div>
        </v-card-text>
        <v-spacer/>
        <v-card-actions>
            <v-spacer/>
            <a v-if="phone != ''" :href="'tel:' + phone" target="_blank" class="mr-1">
                <b-btn icon>
                <v-icon x-large>mdi-phone</v-icon>
                </b-btn>
            </a>
            <a v-if="email != ''" :href="'mailto:' + email" target="_blank" class="mr-1">
                <b-btn icon>
                <v-icon x-large>mdi-email</v-icon>
                </b-btn>
            </a>
            <a v-if="linkedin != ''" :href="linkedin" target="_blank" class="mr-1">
                <b-btn icon>
                <v-icon x-large>mdi-linkedin</v-icon>
                </b-btn>
            </a>
            <a v-if="twitter != ''" :href="twitter" target="_blank" class="mr-1">
                <b-btn icon>
                <v-icon x-large>mdi-twitter</v-icon>
                </b-btn>
            </a>
        </v-card-actions>
    </v-card>
</template>

<script>
export default {
    name: 'Person',
    props: {
        image: {
            type: String,
            default: '/images/person.webp'
        },
        name: {
            type: [String, Boolean],
            default: ''
        },
        degrees: {
            type: String,
            default: ''
        },
        position: {
            type: String,
            default: ''
        },
        bio: {
            type: String,
            default: ''
        },
        phone: {
            type: String,
            default: ''
        },
        email: {
            type: String,
            default: ''
        },
        linkedin: {
            type: String,
            default: ''
        },
        twitter: {
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

.person {
    width: 90%;
}

</style>
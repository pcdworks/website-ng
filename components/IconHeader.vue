<template>
    <v-card-title>
        <v-img :src="image" max-height="150px" max-width="150px" class="icon-image"></v-img>
        <div class="icon-title">{{text}}</div>
    </v-card-title>
</template>

<script>
export default {
    name: 'IconHeader',
    props: {
        image: {
            type: String,
            default: ''
        },
        text: {
            type: String,
            default: ''
        }
    }
}
</script>

<style lang="scss" scoped>

.icon-image {
    display: inline-block;
    max-width: 40%;
}

.icon-title {
    color: #afbc21;
    font-size: 2.4rem;
    font-weight: 600;
    padding-left: 1rem;
    max-width: calc(50% - 1rem);
    display: inline-block;
    white-space: normal;
    word-break: break-word;
}

</style>
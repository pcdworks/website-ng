<template>
    <v-img :src="image" :aspect-ratio="21/9"
    gradient="to top right, rgba(0,0,0,0.5), rgba(0,0,0,0.5)">
        <div class="py-16 px-xl-16 px-lg-16 px-md-4">
            <div class="py-16 px-xl-16 px-lg-16 px-md-4 pa-6">
                <div  class="mx-4">
                    <slot></slot>
                </div>
                <v-tooltip v-for="(highlight, idx) in highlights" :key="idx" top>
                <template #activator="{ on, attrs }">
                    <v-chip
                        color="#5e6e64" text-color="white" class="highlight" label large
                        v-bind="attrs"
                        :href="highlight.link"
                        target="_blank"
                        v-on="on">
                    <span class="highlight text-truncate">{{highlight.text}}</span>
                    </v-chip>
                </template>
                <span>{{highlight.text}}</span>
                </v-tooltip>
            </div>
        </div>
    </v-img>
</template>

<script>
export default {
    name: 'Highlights',
    props: {
        image: {
            type: String,
            default: ''
        },
        highlights: {
            type: Array,
            default: () => []
        }
    },
    setup() {
        
    },
}
</script>

<style lang="scss" scoped>

.highlight {
  text-align: center;
  border: 0;
  outline: 0;
  padding-right: 20px;
  padding-left: 20px;
  display: inline-block;
  transform: skew(-30deg);
  margin: 0 auto;
  max-width: 100%;
  font-weight: 680;
  margin: 6px;
  font-size: 1.2rem;
}

span .highlight {
  display: inline-block;
  width: 100%;
  transform: skew(30deg);
}

::v-deep p,
::v-deep ul,
::v-deep h1,
::v-deep h2 {
    color: white;
}

</style>
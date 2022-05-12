<template>
    <v-img :src="image"  :aspect-ratio="21/9"
    gradient="to top right, rgba(0,0,0,0.5), rgba(0,0,0,0.5)">
        <div class="py-16 px-xl-16 px-lg-16 px-md-4">
            <div class="py-16 px-xl-16 px-lg-16 px-md-4 pa-6">
                <slot></slot>
                <v-tooltip top v-for="(highlight, idx) in highlights" :key="idx">
                <template v-slot:activator="{ on, attrs }">
                    <v-chip
                        color="#5e6e64" text-color="white" class="highlight" label large
                        v-bind="attrs"
                        v-on="on"
                        :to="highlight.link">
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
  padding-right: 44px;
  padding-left: 44px;
  display: inline-block;
  transform: skew(-30deg);
  margin: 0 auto;
  max-width: 100%;
  font-weight: 680;
  margin: 6px;
  font-size: 1.2rem;
}

.highlight:hover {
  opacity: 90%;
}

span .highlight {
  display: inline-block;
  transform: skew(30deg);
}

::v-deep p, ul {
    font-size: 1.2rem;
    font-weight: 500;
    color: white;
    padding-left: 1rem;
    padding-right: 1rem;
}

::v-deep h1 {
    text-transform: uppercase;
    color: white;
    font-size: 4.5rem;
    line-height: 1.1;
    padding-left: 1rem;
    padding-right: 1rem;
}

::v-deep h2 {
    color: white;
    font-size: 3.5rem;
    padding-left: 1rem;
    padding-right: 1rem;
}

@media #{map-get($display-breakpoints, 'md-and-down')} {
  ::v-deep h1{
    font-size:3rem;
  }

  ::v-deep h2 {
    font-size: 1.5rem;
  }

}
</style>
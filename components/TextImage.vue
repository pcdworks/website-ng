<template>
    <div class="py-16 px-xl-16 px-lg-16 px-md-4">
        <v-row class="px-xl-16 px-lg-16 px-md-4">
            <v-col cols="12" xl="6" lg="6" md="6">
                <div class="pa-2">
                    <slot name="left"></slot>
                </div>
            </v-col>
            <v-col cols="12" xl="6" lg="6" md="6">
                <div class="pt-4 px-4 px-xl-16 px-lg-4 px-md-4 px-sm-16">
                    <div :class="trimClass">
                        <v-img :src="image" class="align-end">
                            <div v-if="has_right"
                            class="right-content py-2 px-2 py-lg-10 px-lg-16 py-xl-10 px-xl-16 py-md-8 px-md-6 px-sm-6 py-sm-6">
                                <slot name="right"></slot>
                            </div>
                        </v-img>
                    </div>
                </div>
            </v-col>
        </v-row>
    </div>
</template>

<script>
export default {
    name: 'TextImage',
    props: {
        image: {
            type: String,
            default: ''
        },
        trim: {
            type: Boolean,
            default: false
        },
        has_right: {
            type: Boolean,
            default: false
        }
    },
    computed: {
        trimClass () {
            if (this.trim) {
                return 'trim'
            }
            return ''
        }
    }
}
</script>

<style lang="scss" scoped>

.trim {
    background: linear-gradient(90deg, rgba(255,255,255,0) 50%, #5e6e64 50%);
    padding-top: 3rem;
    padding-bottom: 3rem;
    padding-right: 3rem;
}

::v-deep p, ul {
    font-size: 1.5rem;
    font-weight: 500;
    color: #5e6e64;
    padding-left: 1rem;
    padding-right: 1rem;
}

::v-deep h1 {
    text-transform: uppercase;
    color: #afbc21;
    font-size: 4.5rem;
    line-height: 1.1;
    padding-left: 1rem;
    padding-right: 1rem;
}

::v-deep h2 {
    color: #afbc21;
    font-size: 3.5rem;
    padding-left: 1rem;
    padding-right: 1rem;
}

::v-deep .right-content {
    background: rgba(51, 102, 51, 0.8);
    color: rgba(255,255,255, 1);
    font-size: 1.3rem;
    h2 {
        color: inherit;
        font-size: 2rem;
    }
}

@media #{map-get($display-breakpoints, 'md-and-down')} {
  ::v-deep h1{
    font-size:3rem;
  }

  ::v-deep h2 {
    font-size: 2rem;
  }

  ::v-deep .right-content {
        background: rgba(51, 102, 51, 0.8);
        color: rgba(255,255,255, 1);
        font-size: 1rem;
        h2 {
            color: inherit;
            font-size: 1.2rem;
        }
    }

    .trim {
        padding: 1.5rem;
    }
}
</style>
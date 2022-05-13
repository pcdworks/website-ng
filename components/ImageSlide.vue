<template>
    <v-img :src="image" class="fader" :aspect-ratio="24/9">
        <v-container fluid fill-height class="fader-box">
            <v-row>
                <v-col class="fader-content">
                    <div class="pa-2 py-16 px-xl-16 px-lg-16 px-md-4">
                        <div class="px-xl-16 px-lg-16 px-md-4">
                            <slot></slot>
                        </div>
                    </div>
                </v-col>
            </v-row>
        </v-container>
    </v-img>
</template>

<script>
export default {
    name: 'ImageSlide',
    props: {
        image: {
            type: String,
            default: ''
        }
    }
}
</script>

<style lang="scss" scoped>

::v-deep strong {
    font-weight: 800;
}
::v-deep p {
    font-weight: 600;
}

.fader-box {
    background: rgba(0, 0, 0, 0.7)
}

.fader-content {
    color: rgba(255, 255, 255, 1);
    font-size: 1.6rem;
}

.fader {
    min-height: 580px;
    text-align: center;
    color: white;
    font-weight: 600;
}
::v-deep h2 { 
    font-size: 3rem;
    font-weight: 700;
}

::v-deep h3 { 
    font-size: 3rem;
    font-weight: 370;
}

@media #{map-get($display-breakpoints, 'md-and-down')} {
  ::v-deep h1{
    font-size:3rem;
  }

  ::v-deep h2 {
    font-size: 2rem;
  }

  ::v-deep p {
      font-size: 1rem;
  }

}

</style>
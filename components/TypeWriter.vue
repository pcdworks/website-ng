<template>
    <div id="typewriter"></div>
  </template>
  
  <script>
  import Typewriter from 'typewriter-effect/dist/core'
  
  export default {
      name: 'TypeWriter',
      props: {
          strings: {
              type: Array,
              default: () => []
          }
      },
      mounted() {
          const entry = document.getElementById('typewriter')
          const typewriter = new Typewriter(entry, {
              loop: true,
              strings: this.strings,
              delay: 'natural',
              autoStart: true
          })
          typewriter.start()
      }
  }
  </script>
  
  <style>
  #typewriter {
      font-family: "DroidSansMono",monospace;
  }
  </style>
  
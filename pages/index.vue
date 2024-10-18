<template>
  <div>
    <Navbar />
    <h1>Nuxt.js uygulamamıza hoş geldiniz</h1>
    <p>Bu, uygulamamızın ana sayfasıdır.</p>
    <VideoPlayer :player-type="playerType" :player-config="playerConfig" />
  </div>
</template>

<script setup>
import { ref } from 'vue'
import VideoPlayer from '~/components/VideoPlayer.vue'

const playerType = ref('videojs')
const playerConfig = ref({
  sources: [{
    src: 'https://example.com/video.mp4',
    type: 'video/mp4'
  }]
})
</script>





<!--
<template>
  <div>
    <Navbar />
    <h1>Welcome to Our Nuxt.js App</h1>
    <p>This is the home page of our application.</p>
  </div>
</template>

<script setup>
// Main page logic can be added here
</script>
-->
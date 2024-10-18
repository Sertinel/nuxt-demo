<template>
  <div>
    <h1>Video oynatıcı yönetimi</h1>
    <select v-model="selectedPlayer">
      <option value="videojs">Video.js</option>
      <option value="kaltura">Kaltura Player</option>
      <option value="playerjs">PlayerJS</option>
      <option value="rxplayer">rx-player</option>
      <option value="oplayer">oplayer</option>
    </select>
    <textarea v-model="configJson" rows="10" cols="50"></textarea>
    <button @click="updateConfig">Güncelle</button>
    <VideoPlayer :player-type="selectedPlayer" :player-config="playerConfig" />
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'
import VideoPlayer from '~/components/VideoPlayer.vue'

const selectedPlayer = ref('videojs')
const configJson = ref('{}')
const playerConfig = ref({})

const updateConfig = () => {
  try {
    playerConfig.value = JSON.parse(configJson.value)
  } catch (e) {
    alert('Invalid JSON configuration')
  }
}
</script>

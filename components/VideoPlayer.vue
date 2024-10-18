<template>
  <div>
    <div ref="videoContainer"></div>
  </div>
</template>

<script setup>
import { ref, onMounted, watch } from 'vue'
import videojs from 'video.js'
import { KalturaPlayer } from '@kaltura/kaltura-player-js'
import PlayerJS from 'playerjs'
import { RxPlayer } from 'rx-player'
import OPlayer from 'oplayer'

const props = defineProps(['playerType', 'playerConfig'])
const videoContainer = ref(null)
let player = null

const initPlayer = () => {
  if (player) {
    player.dispose()
  }

  switch (props.playerType) {
    case 'videojs':
      player = videojs(videoContainer.value, props.playerConfig)
      break
    case 'kaltura':
      player = KalturaPlayer.setup(props.playerConfig)
      player.loadMedia({ entryId: props.playerConfig.entryId })
      break
    case 'playerjs':
      player = new PlayerJS(videoContainer.value, props.playerConfig)
      break
    case 'rxplayer':
      player = new RxPlayer(props.playerConfig)
      player.attachMedia(videoContainer.value)
      break
    case 'oplayer':
      player = new OPlayer(videoContainer.value, props.playerConfig)
      break
  }
}

onMounted(() => {
  initPlayer()
})

watch(() => props.playerType, initPlayer)
watch(() => props.playerConfig, initPlayer)
</script>

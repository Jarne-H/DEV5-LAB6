<script setup>
/**import videoplayer.vue*/
import VideoPlayer from './components/VideoPlayer.vue'
import VideoDetails from './components/VideoDetails.vue'
</script>

<template>
  <div class="app">
    <VideoPlayer />
    <VideoDetails />
  </div>
</template>

<style scoped>
.app{
  display: grid;
  grid-template-columns: 8fr 4fr;
}
</style>

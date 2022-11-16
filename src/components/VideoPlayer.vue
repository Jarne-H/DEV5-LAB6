<script setup>
//https://app.fakejson.com/q/Dt6soyE2?token=J8LA1-xpV4FBoiU5vS0n4Q
import { ref, reactive, onMounted } from 'vue'
import 'animate.css';

let src = ref('');
let videos = reactive({ videos: [] });
let animation = ref('');

//onmounted
onMounted(() => {
    console.log('VideoDetails.vue mounted')
    let api_url = "http://127.0.0.1:5173/tiktok.json";
    fetch(api_url)
        .then(response => response.json())
        .then(data => {
          console.log(data);
            src.value = data.videos[0].video;
            videos.videos = data.videos;
        })
});

let nextVideo = () => {
  animation.value = 'animate__fadeOut';
  setTimeout(() => {
    videos.videos.shift();
    src.value = videos.videos[1].video;
    animation.value = 'animate__fadeIn';
  }, 100);
  
}

</script>

<template>
  <div class="video">
    <div class="controls">
      <a @click.prevent="nextVideo" href="#" class="controls__next">
        [🤢]
      </a>
    </div>
    <video :class="animation" class="animate__animated animate__bounce" :src="src" controls autoplay muted>
    </video>
  </div>
</template>

<style scoped>
.video{
    position: relative;
}
.controls{
  position: absolute;
  right: 30%;
  top: 60%;
  z-index: 1;
  background-color: aquamarine;
  text-decoration: none;
  border-radius: 2;
}
</style>

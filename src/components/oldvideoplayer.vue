<script setup>
import { reactive, ref} from 'vue'
let title = ref('Video Title');
let videos = reactive(["video1", "video2", "video3"]);

const addVideo = () => {
    videos.push(title.value);
  console.log(videos);
}   
</script>

<template>
  <div>
    <h1>{{title}}</h1>
    <ul>
      <li v-for="video in videos" :key="video">
        {{video}}
      </li>
    </ul>
    <input type="text" v-model="title">
    <button @click="addVideo">Add video</button>
  </div>
</template>

<style scoped>
</style>
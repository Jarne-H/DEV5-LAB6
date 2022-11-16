<script setup>
import { ref, reactive, onMounted } from 'vue'

let username = ref('');
let description = ref('');

//onmounted
onMounted(() => {
    const api = "http://127.0.0.1:5173/tiktok.json";
    fetch(api)
        .then(response => response.json())
        .then(data => {
            console.log(data);
            //set username
            username.value = data.videos[0].username;
            //set title
            description.value = data.videos[0].description;
        })
});
</script>

<template>
  <div class="videoDetails">
    <h3>{{username}}</h3>
    <p>{{description}}</p>
  </div>
</template>

<style scoped>
.videoDetails{
    padding: 0 1rem;
}
</style>

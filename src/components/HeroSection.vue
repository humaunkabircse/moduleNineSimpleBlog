<script setup>
import {ref, onMounted} from 'vue'

const baseUrl = 'https://basic-blog.teamrabbil.com/api'
const postSlider = ref([''])

async function getPostSlider() {
    const response = await fetch(`${baseUrl}/post-newest`)
    postSlider.value = await response.json()
    console.log(postSlider.value);
}

onMounted(() => {
    getPostSlider()
})
</script>

<template>
  <div class="container-fluid text-center">
    <img :src="postSlider[0]['img']" alt="" class="img-fluid" style="width:100%">
    <h3 class="mt-3">{{ postSlider[0]['title'] }}</h3>
    <p>{{ postSlider[0]['short'] }}</p>
  </div>
</template>


<style scoped>

</style>
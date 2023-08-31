<script setup>
import { ref, onMounted } from 'vue'

const baseUrl = 'https://basic-blog.teamrabbil.com/api'

const allPost = ref([])

async function getAllPost(){
    const response = await fetch(`${baseUrl}/post-newest`)
    allPost.value = await response.json()
}

onMounted(() => {
    getAllPost()
})



</script>

<template>

<div class="container-fluid bg-3 text-center mt-4">    
  <div class="row">
    <div class="col-sm-3" v-for="(item, index) in allPost" :key="index">
      <img :src="item['img']" class="img-responsive" style="width:100%" alt="Image">
      <h4 class="mt-3">{{ item['title'] }}</h4>
      <span>{{ item['short'] }}</span>
    </div>

  </div>
</div>
</template>


<style scoped>

</style>
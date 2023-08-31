<script setup>
import { ref, onMounted } from 'vue'

const baseUrl = 'https://basic-blog.teamrabbil.com/api'

const categoryList = ref('')

async function getCategoryList() {
    const response = await fetch(`${baseUrl}/post-categories`)
    categoryList.value = await response.json()
}

onMounted(() =>{
  getCategoryList()
})


</script>

<template>
    <div class="containter">
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
        <a class="navbar-brand" href="#">Sport Blog</a>
        <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarNav">
            <ul class="navbar-nav">
                <li class="nav-item"><a class="nav-link" href="/">হোম</a> </li>
                <template v-for="(category, index) in categoryList" :key="index">
                  <li class="nav-item"><a class="nav-link" href="">{{ category['name'] }}</a> </li>
                </template>
            </ul>
        </div>
    </nav>
</div>
</template>


<style scoped>

</style>
<template>
    <div>
        <h1 v-if="isShow">
           Rikkei Academi 
        </h1>
        <button @click="handletoggle">Hiện</button>
    </div>
</template>

<script setup>
import {ref} from "vue"
    const isShow = ref(false)
    const handletoggle=()=>{
        return isShow.value = !isShow.value
    }
</script>

<style>

</style>
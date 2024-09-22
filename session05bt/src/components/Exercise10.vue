<template>
    <div>
    <button @click="handlePush">push</button>
    <h1>{{arrNumber}}</h1>
  </div>
</template>

<script setup>
import {ref} from "vue"
    let count = ref(0);
    let random = ref(Math.floor(Math.random()*10))
    const handelRandom=()=>{
        random.value = ref(Math.floor(Math.random()*10))
    }
    const arrNumber = ref([])   
    const handlePush=()=>{
        handelRandom()
        arrNumber.value.push(random.value)
        
    }
</script>

<style>

</style>
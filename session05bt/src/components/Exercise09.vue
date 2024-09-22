<template>
    <div>
        <div v-if="gender === 0">Gender: Nam</div>
        <div v-if="gender === 1">Gender: Nữ</div>
        <div v-if="gender === 2">Gender: Khác</div>
        <button @click="randomGender">Random gender</button>
    </div>
</template>

<script setup>
    import {ref} from "vue"
    const gender = ref(0)
    const randomGender=()=>{
        gender.value = Math.floor(Math.random()*3)
    }
</script>

<style>

</style>
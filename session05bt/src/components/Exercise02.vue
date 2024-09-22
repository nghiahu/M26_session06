<template>
    <div>
        <button @click="handletoggleTwo" v-if="isShowTwo">Hiện</button>
        <button @click="handletoggleTwo" v-else>Ẩn</button>
    </div>
</template>

<script setup>
import {ref} from "vue"
    const isShowTwo = ref(true)
    const handletoggleTwo=()=>{
        return isShowTwo.value = !isShowTwo.value
    }
</script>

<style>

</style>
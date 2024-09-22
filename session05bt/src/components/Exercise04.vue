<template>
  <div>
    <div>
        <button @click="handelVisible">Hiển thị</button>
        <button @click="handeUnlVisible">Ẩn</button>
    </div>
    <h3 v-show="isVisible">Thông báo: Welcome to Rekkei Academy</h3>
  </div>
</template>

<script setup>
import {ref} from "vue"
    const isVisible = ref(true)
    const handelVisible=()=>{
      return isVisible.value = true
    }
    const handeUnlVisible=()=>{
      return isVisible.value = false
    }
</script>

<style>

</style>
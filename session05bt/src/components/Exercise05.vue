<template>
  <div>
    Các mảng số chẵn: [
    <label v-for="(number, index) in array" :key="index">{{number%2===0? number+", " : ""}}
    </label>
    ]
  </div>
</template>

<script setup>
  const array = [1, 2, 3, 4, 5, 6, 7, 8, 9];
</script>

<style>
</style>

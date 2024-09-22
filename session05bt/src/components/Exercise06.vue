<template>
  <div>
    <p>Mảng các số lẻ chia hết cho 3 và lớn hơn 10</p>
      [<label v-for="num in filteredArr" :key="num">{{ num }},</label>]
  </div>
</template>

<script setup>
import { reactive, computed } from "vue"

const arr = reactive([2, 3, 12, 15, 22, 26, 30, 33, 38])

const filteredArr = computed(() => {
  return arr.filter(num => num % 3 === 0 && num > 10 && num % 2 !== 0)
})
</script>

<style>

</style>

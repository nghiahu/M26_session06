<template>
<div>
    <div>
        <button @click="sortAsc">Tăng dần</button>
        <button @click="sortDesc">Giảm dần</button>
    </div>
    <br>
    <button v-for="(number, index) in arrNumber" :key="index">
        {{number}}
    </button>

</div>
</template>

<script setup>
import {ref} from "vue"
    const arrNumber = ref([1,5,8,3,7,2,9,6])
    const sortAsc = () => {
  arrNumber.value = [...arrNumber.value].sort((a, b) => a - b);
};

const sortDesc = () => {
  arrNumber.value = [...arrNumber.value].sort((a, b) => b - a);
};
</script>

<style>

</style>
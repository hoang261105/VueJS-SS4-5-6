<template>
  <p>Các số chắn từ mảng: {{ result.join(" ") }}</p>
</template>

<script setup>
import { ref } from "vue";

const arr = ref([1, 2, 3, 4, 5, 6, 7, 8, 9, 10]);
const result = arr.value.filter((number) => number % 2 === 0);
</script>

<style></style>

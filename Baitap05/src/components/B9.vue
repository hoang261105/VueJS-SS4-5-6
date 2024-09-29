<template>
  <div>
    <p>Giới tính: {{ result }}</p>
    <button @click="handleClick">Random Gender</button>
  </div>
</template>

<script setup>
import { ref } from "vue";

const arr = ["Nam", "Nữ", "Khác"];
const result = ref(arr[0]);
const handleClick = () => {
  const randomIndex = Math.floor(Math.random() * arr.length);
  result.value = arr[randomIndex];
};
</script>

<style></style>

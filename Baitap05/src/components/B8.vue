<template>
  <div>
    <button @click="handleIncrease">Tăng dần</button>
    <button @click="handleDecrease">Giảm dần</button><br />
    <p>{{ arr.join(" ") }}</p>
  </div>
</template>

<script setup>
import { ref } from "vue";

const arr = ref([1, 2, 5, 4, 9, 8, 7]);
const handleIncrease = () => {
  arr.value.sort((a, b) => a - b);
};

const handleDecrease = () => {
  arr.value.sort((a, b) => b - a);
};
</script>

<style></style>

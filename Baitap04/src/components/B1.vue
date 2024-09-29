<template>
  <button @click="handleIncrease">Click {{ count }} lần</button>
</template>

<script setup>
import { ref } from "vue";
const count = ref(0);
const handleIncrease = () => {
  count.value += 1;
};
</script>

<style></style>

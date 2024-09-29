<template>
  <div>
    <p>[{{ arr.join(",") }}]</p>
    <button @click="handleClick">Random Number</button>
  </div>
</template>

<script setup>
import { ref } from "vue";

const arr = ref([]);
const handleClick = () => {
  arr.value = [...arr.value, Math.floor(Math.random() * 100)];
};
</script>

<style></style>

<template>
  <div>
    <button @click="handleClick">Hiện</button>
    <p v-show="isShow">Rikkei Education</p>
  </div>
</template>

<script setup>
import { ref } from "vue";

const isShow = ref(false);

const handleClick = () => {
  isShow.value = !isShow.value;
};
</script>

<style></style>

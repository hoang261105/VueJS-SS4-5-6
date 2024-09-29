<template>
  <div>
    <button @click="handleShow">Hiện</button>
    <button @click="handleHide">Ẩn</button>
    <p v-if="isVisible">Thông báo: <b>Welcome to Rikkei Education</b></p>
  </div>
</template>

<script setup>
import { ref } from "vue";

const isVisible = ref(false);

const handleShow = () => {
  isVisible.value = true;
};

const handleHide = () => {
  isVisible.value = false;
};
</script>

<style></style>

<template>
  <div>
    <button @click="handleShow">Hiển thị</button>
    <button @click="handleHide">Ẩn</button> <br />
    <b v-if="isVisible">Nội dung được hiển thị</b>
    <b v-else>Nội dung bị ẩn</b>
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

<template>
  <div>
    <button @click="handleShow" v-if="!isShow">Hiện</button>
    <button @click="handleHide" v-if="isShow">Ẩn</button>
  </div>
</template>

<script setup>
import { ref } from "vue";

const isShow = ref(false);

const handleShow = () => {
  isShow.value = true;
};

const handleHide = () => {
  isShow.value = false;
};
</script>

<style></style>

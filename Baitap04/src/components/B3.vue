<template>
  <div>
    <p>Width: {{ width }}</p>
    <p>Height: {{ height }}</p>
    <p>Diện tích: {{ area }}</p>
    <button @click="handleChange">Change data</button>
  </div>
</template>

<script setup>
import { ref } from "vue";

const width = ref(10);
const height = ref(20);
const area = ref(width.value * height.value);
// Cứ mỗi lần click thay đổi thì tăng width lên 10
const handleChange = () => {
  width.value += 10;
  area.value = width.value * height.value;
};
</script>

<style></style>

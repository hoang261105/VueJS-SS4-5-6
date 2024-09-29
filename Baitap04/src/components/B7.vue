<template>
  <div>
    <p>Giá trị: {{ number }}</p>
    <p>Bình phương: {{ square }}</p>
    <button @click="handleIncrease">Click</button>
  </div>
</template>

<script setup>
import { computed, ref, watch } from "vue";

const number = ref(0);
const square = computed(() => number.value ** 2);

const handleIncrease = () => {
  number.value++;
};

watch(number, (newValue, oldValue) => {
  console.log(`Giá trị mới: ${newValue}, Giá trị cũ: ${oldValue}`);
});
</script>

<style></style>

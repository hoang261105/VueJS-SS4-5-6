<template>
  <input type="text" @input="handleChange" />
</template>

<script setup>
import { ref, watch } from "vue";

const inputText = ref("");
watch(inputText, (newValue, oldValue) => {
  console.log(`Giá trị thay đổi từ ${oldValue} thành ${newValue}`);
});
const handleChange = (e) => {
  inputText.value = e.target.value;
};
</script>

<style></style>

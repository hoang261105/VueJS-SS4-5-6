<template>
  <div>
    <p>Company: {{ data.company }}</p>
    <p>Age: {{ data.age }}</p>
    <button @click="handleChange">Change data</button>
  </div>
</template>

<script setup>
import { reactive } from "vue";
const data = reactive({
  company: "Rikkei Academy",
  age: 20,
});

const handleChange = () => {
  (data.company = "Rikkei Education"), (data.age = 21);
};
</script>

<style></style>

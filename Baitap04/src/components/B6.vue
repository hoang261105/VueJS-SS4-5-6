<template>
  <div>
    <input type="number" @input="handleChange" v-model="price" />
    <button @click="handleClick">Add To Cart</button>
    <p>Tổng số tiền trong giỏ hàng: {{ total }}</p>
  </div>
</template>

<script setup>
import { ref } from "vue";

const price = ref(0);
const total = ref(0);

const handleChange = (e) => {
  price.value = Number(e.target.value);
};

const handleClick = () => {
  total.value += price.value;
  price.value = 0;
};
</script>

<style></style>

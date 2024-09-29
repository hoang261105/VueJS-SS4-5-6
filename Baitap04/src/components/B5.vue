<template>
  <div>
    <ul>
      <li v-for="product in products" :key="product.id">
        {{ product.name }} - Số lượng: {{ product.quantity }}
        <button @click="handleClick(product.id)">Tăng số lượng</button>
      </li>
    </ul>
    <p>Tổng số lượng : {{ totalQuantity }}</p>
  </div>
</template>

<script setup>
import { ref, watch } from "vue";

const products = ref([
  {
    id: 1,
    name: "Mèn mén loại 1",
    quantity: 1,
  },
  {
    id: 2,
    name: "Mèn mén loại 2",
    quantity: 2,
  },
  {
    id: 3,
    name: "Mèn mén loại 3",
    quantity: 3,
  },
]);
const totalQuantity = ref(6);
const handleClick = (id) => {
  // Tăng số lượng cho sản phẩm có id tương ứng
  products.value.forEach((product) => {
    if (product.id === id) {
      product.quantity++;
    }
  });
};
watch(
  products,
  () => {
    totalQuantity.value = products.value.reduce(
      (acc, product) => acc + product.quantity,
      0
    );
  },
  { deep: true } // Đảm bảo theo dõi sự thay đổi sâu trong object
);
</script>

<style></style>

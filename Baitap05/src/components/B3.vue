<template>
  <p v-if="adminRole">Quyền hạn của bạn là: {{ adminRole }}</p>
</template>

<script setup>
import { ref } from "vue";

const adminRole = ref("user");
</script>

<style></style>

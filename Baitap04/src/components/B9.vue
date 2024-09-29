<template>
  <div>
    <h2>Danh sách bài viết</h2>
    <div v-for="post in posts" :key="post.id">
      <p>Id: {{ post.id }}</p>
      <p>Title: {{ post.title }}</p>
      <p>Content: {{ post.content }}</p>
      <p>Author: {{ post.author }}</p>
      <p>_____________________________________</p>
    </div>
  </div>
</template>

<script setup>
const posts = [
  {
    id: 1,
    title: "Tại sao nên học React?",
    content: "Học react để đi làm",
    author: "David",
  },
  {
    id: 2,
    title: "Tại sao nên học Vue?",
    content: "Học vue để đi làm",
    author: "John",
  },
  {
    id: 3,
    title: "Tại sao nên học Angular?",
    content: "Học angular để đi làm",
    author: "Jane",
  },
];
</script>

<style></style>

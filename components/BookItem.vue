<!-- Display data of a book with type {title: 'The Name of the Wind', author: 'Patrick Rothfuss', year: 2007},-->
<script setup lang="ts">
import type { Book } from '~/appTypes';
const props = defineProps<{
  book: Book;
}>();
</script>
<template>
  <div class="book-item">
    <h2 class="book-item__title">{{ book.title }}</h2>
    <p class="book-item__author">{{ book.author }}</p>
    <p class="book-item__year">{{ book.year }}</p>
  </div>
</template>

<style scoped>
.book-item {
  padding: 1rem;
  border-bottom: 1px solid #ccc;
}
.book-item__title {
  font-size: 1.5rem;
  font-weight: 300;
  margin: 0;
}
.book-item__author {
  font-size: 1.2rem;
  font-weight: 300;
  margin: 0;
}
.book-item__year {
  font-size: 1rem;
  font-weight: 300;
  margin: 0;
}
</style>

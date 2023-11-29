<script setup lang="ts">
import { ref, computed } from 'vue'
import BookItem from "./BookItem.vue"
import { type Book } from '~/appTypes'
// accept books array as props
const props = defineProps<{
  books: Book[]
}>();

// DATA
const allBooks = ref(props.books)
const searchString = ref<string>('')

// COMPUTED
const filteredBooks = computed(() => {
    return allBooks.value.filter(book => {
        return book.title.toLowerCase().includes(searchString.value.toLowerCase())
    })
})

// METHODS
const sortAscending = () => {
    allBooks.value = filteredBooks.value.sort((a, b) => {
        if (a.title < b.title) {
            return -1
        }
        if (a.title > b.title) {
            return 1
        }
        return 0
    })
}

const sortDescending = () => {
    allBooks.value= filteredBooks.value.sort((a, b) => {
        if (a.title < b.title) {
            return 1
        }
        if (a.title > b.title) {
            return -1
        }
        return 0
    })
}
</script>

<template>
  <div class="book-search">
    <div class="book-search__input">
      <input
        v-model="searchString"
        type="text"
        placeholder="Search for a book"
      />
    </div>

    <!-- Buttons for sorting ascending or descending -->
    <div class="book-search__sort">
      <button class="btn btn--primary mr-1" @click="sortAscending">
        Sort Ascending
      </button>
      <button class="btn btn--primary" @click="sortDescending">
        Sort Descending
      </button>
    </div>
    <div class="book-search__results">
      <BookItem v-for="book in filteredBooks" :key="book.title" :book="book" />
    </div>
  </div>
</template>

<style scoped>
.btn {
  padding: 0.5rem 1rem;
  border-radius: 0.25rem;
  font-size: 1rem;
  font-weight: 300;
  cursor: pointer;
}
.btn--primary {
  background-color: #48bb78;
  color: #fff;
  border: 1px solid #48bb78;
}
.btn--primary:hover {
  background-color: #38a169;
  border-color: #38a169;
}
.book-search--sort {
  margin-bottom: 1rem;
}

.book-search {
  padding: 1rem;
}
.book-search__input {
  margin-bottom: 1rem;
}
.book-search__input input {
  width: 100%;
  padding: 0.5rem;
  font-size: 1rem;
  border: 1px solid #ccc;
  border-radius: 0.25rem;
}
.book-search__results {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  grid-gap: 1rem;
}
</style>

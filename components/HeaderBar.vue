<script lang="ts" setup>
const emit = defineEmits(['search-clicked', 'about-clicked'])
</script>

<template>
  <div class="header">
    <span class="header__title text-green-500">Book Search</span>
    <div class="header__buttons">
      <button
        @click="emit('search-clicked')"
        class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded mr-1"
      >
        Search
      </button>
      <button
        @click="emit('about-clicked')"
        class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded"
      >
        About
      </button>
    </div>
  </div>
</template>
<style scoped>
.header {
  background-color: #f5f5f5;
  border-bottom: 1px solid #ccc;
  position: sticky;
  top: 0;
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem;
}
.header__title {
  font-size: 2rem;
  font-weight: 300;
  text-align: center;
  margin: 0;
}
.header__buttons {
  padding: 0.5rem 1rem;
}
</style>

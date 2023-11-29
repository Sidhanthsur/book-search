<script lang="ts" setup>
import HeaderBar from './components/HeaderBar.vue'
import Footer from './components/Footer.vue'
import BookSearch from './components/BookSearch.vue'
import About from './components/About.vue'
import { Page } from './appTypes'
const books = [
    {title: 'The Name of the Wind', author: 'Patrick Rothfuss', year: 2007},
    {title: 'The Way of Kings', author: 'Brandon Sanderson', year: 2010},
    {title: 'Good Omens', author: 'Terry Pratchett and Neil Gaiman', year: 1990},
    {title: 'The Eye of the World', author: 'Robert Jordan', year: 1990},
    {title: 'The Final Empire', author: 'Brandon Sanderson', year: 2006},
    {title: 'The Well of Ascension', author: 'Brandon Sanderson', year: 2007},
    {title: 'The Hero of Ages', author: 'Brandon Sanderson', year: 2008},
    {title: 'The Alloy of Law', author: 'Brandon Sanderson', year: 2011},
    {title: 'The Bands of Mourning', author: 'Brandon Sanderson', year: 2016},
    {title: 'Shadows of Self', author: 'Brandon Sanderson', year: 2015},
    {title: 'Warbreaker', author: 'Brandon Sanderson', year: 2009},
    {title: 'Elantris', author: 'Brandon Sanderson', year: 2005},
    {title: 'The Emperor\'s Soul', author: 'Brandon Sanderson', year: 2012},
    {title: 'The Rithmatist', author: 'Brandon Sanderson', year: 2013},
]

const page = ref<Page>(Page.SEARCH)
</script>

<template>
  <div>
    <HeaderBar
      @search-clicked="page = Page.SEARCH"
      @about-clicked="page = Page.ABOUT"
    />
    <main>
      <BookSearch v-if="page === Page.SEARCH" :books="books" />
      <About v-else />
    </main>
    <Footer />
  </div>
</template>

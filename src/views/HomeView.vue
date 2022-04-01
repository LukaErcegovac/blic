<template>
  <div class="home">
    <ul>
      <li v-for="book in books" :key="book.url" @click="showabout(book.url)">
        {{book.url}}
      </li>
    </ul>
  </div>
</template>

<script>

import axios from 'axios'
export default {
  name: 'HomeView',

  data: function(){
    return{
      books: []
    }
  },

  methods:{
    showabout(url){
      this.$router.push({name: 'about', params: {url:url}})
    }
  },

  mounted(){
    axios.get('https://www.anapioficeandfire.com/api/books')
      .then(response => {this.books = response.data; console.log(this.books)})
  }
}
</script>

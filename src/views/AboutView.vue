<template>
  <div class="About">
   {{url}}
  </div>
</template>

<script>
import axios from 'axios'

export default{
  name: 'AboutView',

  data: function(){
    return{
      url:""
    }
  },

  mounted(){
    this.url = this.$route.params.url

    axios.get('https://www.anapioficeandfire.com/api/books' + this.$route.params.url)
      .then(response => {this.books = response.data; console.log(this.books)})

  }
}
</script>


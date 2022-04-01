<template>
  <div class="home">
    <ul>
      <li v-for="item in books" :key="item.url" @click="showabout(item.url)">
        {{item.url}}
      </li>
    </ul>
  </div>
</template>

<script>

export default {
  name: 'HomeView',

  data: function(){
    return{
      books: []
    }
  },

  async mounted(){
    let rez = await fetch("https://www.anapioficeandfire.com/api/books")
    let pod = await rez.json()

    for(let item of pod){
      console.log(item.url)
    }

    this.books = pod
  }
}
</script>

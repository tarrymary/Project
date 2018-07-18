<template>
    <v-layout class="library">
      <div class="library__content" v-for='book in books' :key="book.id">
        <lable>{{ book.title }}</lable>
        <div>Жанр: {{ book.genre }}</div>
        <div>Год: {{ book.year }}</div>
      </div>
    </v-layout>
</template>

<script>
export default {
data() {
    return {
        books: [
        ]
    }
},
 created() {
    axios.get("https://onlinereader.herokuapp.com/api/books").then(res => {
      if(res.data.status === 'OK') {
        this.books = res.data.data;
      }
    });
  }
}
</script>

<style>
    .flex {
        height: 0;
    }
    .v-content__wrap {
        height: 0;
    }
    .library {
        height: 220px;
        border: 1px solid #000;
        display: flex;
        flex-direction: row;
        justify-content: space-around;
        align-items: start;
    }
    .library__content {

    }
    
    lable {
        font-size: 15pt;
    }
</style>

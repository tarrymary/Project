<template>
    <v-layout class="library">
      <div class="library__content" v-for='book in books' :key="book.id">
        <v-card>
          <v-card-title primary-title>
            <div>
              <div class="book-name">{{book.title}}</div>
              <div>Жанр: {{ book.genre }}</div>
            </div>
          </v-card-title>
          <v-card-actions>
            <v-btn v-bind:href="book.book" download flat>Скачать</v-btn>
          </v-card-actions>
        </v-card>
        
      </div>
    </v-layout>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      books: []
    };
  },
  methods: {},

  created() {
    axios.get("https://onlinereader.herokuapp.com/api/books").then(res => {
      this.books = res.data;
    });
  }
};
</script>

<style>
.library {
  padding: 10px 50px;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: space-between;
  align-items: flex-start;
}

.library__content {
  padding: 0 10px 10px 0;
  flex-basis: 25%;
}

.book-name {
  text-decoration: none;
  font-size: 12pt;
  color: #4CAF50;
}

</style>

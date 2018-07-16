<template>
  <v-container fluid class="px-0 pt-0">
    <v-btn @click="getUsers">get users</v-btn>
    <br>
    <v-btn @click="putUser">put user</v-btn>
    <v-btn @click="getUser">get user</v-btn>
    <br>
    <v-btn @click="getBooks">get books</v-btn>
    <v-btn @click="$refs.bookInput.click()">Загрузить книгу</v-btn>
    <input @change="postBooks" ref="bookInput" type="file" style="display: none">
    <br>
    <v-btn @click="putBook">put book</v-btn>
    <v-btn @click="getBook">get book</v-btn>
    <v-btn @click="deleteBook">delete book</v-btn>
  </v-container>
</template>

<script>
import axios from "axios";
export default {
  methods: {
    getUsers() {
      axios.get("https://onlinereader.herokuapp.com/api/users").then(res => {});
    },
    putUser() {
      let fd = new FormData();
      fd.append();
      /* ... */
      axios
        .put("https://onlinereader.herokuapp.com/api/users/:id", fd)
        .then(res => {});
    },
    getUser() {
      axios
        .get("https://onlinereader.herokuapp.com/api/users/:id")
        .then(res => {});
    },
    deleteUser() {
      axios
        .delete("https://onlinereader.herokuapp.com/api/users/:id")
        .then(res => {});
    },
    getBooks() {
      axios.get("https://onlinereader.herokuapp.com/api/books").then(res => {});
    },
    postBooks(e) {
      console.log(e.target.files)
      let fd = new FormData();
      fd.append('book', e.target.files);
      /* ... */

      axios
        .post("https://onlinereader.herokuapp.com/api/books", fd)
        .then(res => {});
    },
    putBook() {
      let fd = new FormData();
      fd.append();
      /* ... */

      axios
        .put("https://onlinereader.herokuapp.com/api/books/:id")
        .then(res => {});
    },
    getBook() {
      axios
        .get("https://onlinereader.herokuapp.com/api/books/:id")
        .then(res => {});
    },
    deleteBook() {
      axios
        .delete("https://onlinereader.herokuapp.com/api/books/:id")
        .then(res => {});
    }
  }
};
</script>

<style scoped>
h1,
h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>

<template>
  <v-container fluid class="px-0 pt-0">
    <v-layout>
      <v-btn @click="getUsers">get users</v-btn>
      <v-btn @click="putUser">put user</v-btn>
      <v-btn @click="getUser">get user</v-btn>
      <v-btn @click="$refs.bookInput.click()">Загрузить книгу</v-btn>
      <input @change="postBooks" ref="bookInput" type="file" style="display: none">
      <v-btn @click="putBook">put book</v-btn>
      <v-btn @click="getBook">get book</v-btn>
    </v-layout>
    
    <div v-if='isSuccess'>Все хорошо</div>
    <div v-if='!isSuccess'>{{ errorMessage }}</div>
  </v-container>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      isSuccess: false,
      errorMessage: ''
    }
  },

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
    postBooks(e) {
      let file = {
          'lastMod'    : e.target.files[0].lastModified,
          'lastModDate': e.target.files[0].lastModifiedDate,
          'name'       : e.target.files[0].name,
          'size'       : e.target.files[0].size,
          'type'       : e.target.files[0].type
      }

      axios
        .post("https://onlinereader.herokuapp.com/api/books", file)
        .then(res => {
          if(res.data.status === 'OK') {
            this.isSuccess = true;
          } else {
            this.isSuccess = false;
            this.errorMessage = res.data.message
          }
        })
        .catch(e => {
          alert(e);
        })
    },
    putBook() {
      let fd = new FormData();
      fd.append();

      axios
        .put("https://onlinereader.herokuapp.com/api/books/:id")
        .then(res => {});
    },
    getBook() {
      axios
        .get("https://onlinereader.herokuapp.com/api/books/:id")
        .then(res => {});
    }
  }
}
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

.books-img {
  width:80px;
}
</style>

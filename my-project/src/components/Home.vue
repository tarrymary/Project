<template>
  <v-container fluid class="px-0 pt-0">
    <v-layout row justify-center>
      <v-flex xs2>
        <v-form v-model="valid">
          <v-text-field label="Название книги"
          v-model="name"
          :rules="nameRules"
          required></v-text-field>
          <v-text-field label="Жанр"
          v-model="genre"
          :rules="nameRules"
          required></v-text-field>
          <v-btn @click="$refs.bookInput.click()" :disabled="!valid">Загрузить книгу</v-btn>
          <input @change="postBooks" ref="bookInput" type="file" style="display: none"> 
        </v-form>
      </v-flex>
      <!-- <v-btn @click="getUsers">get users</v-btn>
      <v-btn @click="putUser">put user</v-btn>
      <v-btn @click="getUser">get user</v-btn>
      <v-btn @click="putBook">put book</v-btn>
      <v-btn @click="getBook">get book</v-btn> -->
    </v-layout>
  </v-container>
</template>

<script>
import axios from "axios";
import router from "../router";

export default {
  data() {
    return {
      valid: false,
      name: "",
      genre: "",
      nameRules: [v => !!v || "Name is required"]
    };
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
      let reader = new FileReader();
      reader.onloadend = () => {
        this.createBook(reader.result);
      };
      reader.readAsDataURL(e.target.files[0]);
    },

    createBook(book) {
      let file = {
        title: this.name,
        genre: this.genre,
        year: this.year,
        rating: 5,
        book: book,
        picture: 1
      };

      axios
        .post("https://onlinereader.herokuapp.com/api/books", file)
        .then(res => {
          if (res.data.status === "OK") {
            router.push('/library');
          }
        });
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

.books-img {
  width: 80px;
}
</style>

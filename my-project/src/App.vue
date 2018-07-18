<template>
  <v-app dark>
    <v-layout row>
      <v-flex>
        <v-toolbar dense>
          <v-btn class="logo__btn" flat icon color="gray lighten" to='/'>
            <img>Home
          </v-btn>
          <v-spacer></v-spacer>
          <v-toolbar-items scroll-toolbar-off-screen class="hidden-sm-and-down" >
            <v-btn class="toolbar__btn" flat to="/library">Library</v-btn>
            <v-btn class="toolbar__btn" flat to="/authors">Authors</v-btn>
            <v-btn class="toolbar__btn" flat>Search</v-btn> 
            <v-btn class="toolbar__btn"  flat to='/signin'>Log In</v-btn>
            <v-btn class="toolbar__btn" flat to='/signup'>Sign Up</v-btn>
          </v-toolbar-items>
        </v-toolbar>
        <div class="bg-img"></div>
      </v-flex>
    </v-layout>
    <v-content>
      <router-view/>
    </v-content>
      <v-footer class="pa-3">
        <v-spacer></v-spacer>
        <div>&copy; {{ new Date().getFullYear() }}</div>
      </v-footer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {

    };
  }
};
</script>

<style>
/* .flex {
  height: 0;
} */

html {
  font-size: 62.5%;
}

.v-toolbar__content {
  background-color: #000;
  color: #fff;
}

.toolbar__btn .v-btn__content {
  color: #fff;
}

.logo__btn .v-btn__content {
  color: #fff;
}

.bg-img {
  background-image: url(assets/background.jpg);
  background-size: cover;
  height: 205px;
}
</style>
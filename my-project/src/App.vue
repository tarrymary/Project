<template>
  <v-app dark>
    <v-layout row>
      <v-flex>
        <v-toolbar dense>
          <v-btn class="logo__btn" flat icon color="gray lighten" to='/'>
            <img>Logo
          </v-btn>
          <v-spacer></v-spacer>
          <v-toolbar-items scroll-toolbar-off-screen class="hidden-sm-and-down" >
            <!-- <v-menu offset-y>
              <v-btn flat
                slot="activator"
              >
                Menu
              </v-btn>
              <v-list>
                <v-list-tile
                  v-for="(item, index) in items"
                  :key="index"
                >
                  <v-list-tile-title>{{ item.title }}</v-list-tile-title>
                </v-list-tile>
              </v-list>
            </v-menu> -->
            <v-btn class="toolbar__btn" flat to='/signin'>Log In</v-btn>
            <v-btn class="toolbar__btn" flat to='/signup'>Sign Up</v-btn>
          </v-toolbar-items>
        </v-toolbar>
        <div class="bg-img"></div>
      </v-flex>
    </v-layout>
    <v-layout row>  
      <v-flex>
        <v-toolbar dense>
          <v-toolbar-items class="second-toolbar">
              <v-btn flat to="/authors">Authors</v-btn>
              <v-btn flat>Genres</v-btn>
              <v-btn flat>Search</v-btn> 
          </v-toolbar-items>
        </v-toolbar>
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
      fixed: false,
      items: [
        { title: "Click Me" },
        { title: "Click Me" },
        { title: "Click Me" },
        { title: "Click Me 2" }
      ]
    };
  },
  name: "App"
};
</script>

<style>
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
.v-toolbar__content .second-toolbar {
  margin: auto;
}
</style>
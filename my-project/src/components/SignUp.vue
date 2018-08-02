<template> 
  <v-layout row justify-center>
    <v-flex xs2>
        <v-form v-model="valid">
          <v-text-field
            v-model="name"
            :rules="nameRules"
            :counter="10"
            label="Login"
            required></v-text-field>
          <v-text-field 
            v-model="email"
            :rules="emailRules"
            label="E-mail"
            required></v-text-field>
          <v-text-field
            v-model="password"
            :append-icon="show1 ? 'visibility_off' : 'visibility'"
            :rules="[rules.required, rules.min]"
            :type="show1 ? 'text' : 'password'"
            name="input-10-1"
            label="Password"
            hint="At least 8 characters"
            counter
            @click:append="show1 = !show1"
          ></v-text-field>
          <v-btn @click='onRegister' color=""
              :disabled="!valid">
              Регистрация
          </v-btn>
        </v-form>
      </v-flex>
  </v-layout>
</template>

<script>
import axios from "axios";
import router from "../router";

export default {
  data() {
    return {
      valid: false,
      name: "",
      nameRules: [
        v => !!v || "Name is required",
        v => v.length <= 10 || "Name must be less than 10 characters"
      ],
      email: "",
      emailRules: [
        v => !!v || "E-mail is required",
        v => /.+@.+/.test(v) || "E-mail must be valid"
      ],
      show1: false,
      show2: true,
      show3: false,
      show4: false,
      password: "",
      rules: {
        required: value => !!value || "Required.",
        min: v => v.length >= 8 || "Min 8 characters"
      }
    };
  },
  methods: {
    onRegister() {
      let fd = new FormData();
      fd.append("login", this.name);
      fd.append("email", this.email);
      fd.append("password", this.password);
      

      axios
        .post("https://onlinereader.herokuapp.com/api/users", fd)
        .then(res => {
          if (res.data.status === "OK") {
            router.push('/');
          }
        });
    },
  }
};
</script>
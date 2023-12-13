<template>
  <v-container>
    <v-row>
      <v-col>
        <v-text>Create User</v-text>
        <v-form @submit.prevent="createUser">
          <v-text-field v-model="newUser.name" label="Name"></v-text-field>
          <v-text-field
            v-model="newUser.surname"
            label="Surname"
          ></v-text-field>
          <v-text-field v-model="newUser.phone" label="Phone"></v-text-field>
          <v-text-field v-model="newUser.email" label="Email"></v-text-field>
          <v-btn type="submit">Create</v-btn>
        </v-form>
        <!-- Пример использования формы -->
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      newUser: {
        name: "",
        phone: "",
        email: "",
        surname: "",
      },
    };
  },
  methods: {
      // метод на создание юзера в бд 
    async createUser() {
      try {
        await axios.post("http://localhost:3111/user", this.newUser);
        window.location.reload();
      } catch (error) {
        console.error("Error creating user:", error);
      }
    },
  },
};
</script>

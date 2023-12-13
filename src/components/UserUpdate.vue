<template>
  <v-container>
    <v-row>
      <v-col>
        <v-text>Update User</v-text>
        <v-form @submit.prevent="updateUser">
          <v-text-field v-model="userId" label="User ID"></v-text-field>
          <v-text-field v-model="updatedUser.name" label="Name"></v-text-field>
          <v-text-field
            v-model="updatedUser.surname"
            label="Surname"
          ></v-text-field>
          <v-text-field
            v-model="updatedUser.phone"
            label="Phone"
          ></v-text-field>
          <v-text-field
            v-model="updatedUser.email"
            label="Email"
          ></v-text-field>
          <v-btn type="submit">Update</v-btn>
        </v-form>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      userId: "",
      updatedUser: {
        name: "",
        phone: "",
        email: "",
        surname: "",
      },
    };
  },
  methods: {
    // обновления поля юзера

    async updateUser() {
      try {
        await axios.put(
          `http://localhost:3111/users/${this.userId}`,
          this.updatedUser
        );
        window.location.reload();
      } catch (error) {
        console.error("Error updating user:", error);
      }
    },
  },
};
</script>

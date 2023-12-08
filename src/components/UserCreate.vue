<template>
  <v-container>
    <v-row>
      <v-col>
        <div class="title">
          <v-text>Create User</v-text>
        </div>
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
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
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
    async createUser() {
      try {
        const response = await this.$axios.post(
          "http://localhost:3000/user",
          this.newUser
        );
        console.log(response.data);
        this.newUser = {
          name: "",
          phone: "",
          email: "",
          surname: "",
        };
        window.location.reload();
      } catch (error) {
        console.error("Error creating user:", error);
      }
    },
  },
};
</script>

<style scoped></style>

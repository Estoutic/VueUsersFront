<template>
    <v-container>
      <v-row>
        <v-col>
          <div class="title">
            <v-text>Delete User by ID</v-text>
          </div>
  
          <v-text-field v-model="deleteId" label="Enter User ID"></v-text-field>
          <v-btn @click="deleteUser">Delete</v-btn>
        </v-col>
      </v-row>
  
      <v-row>
        <v-col>
          <v-text>Result</v-text>
          <v-text v-if="deleteResult">{{ deleteResult }}</v-text>
          <v-text v-else> No user deleted</v-text>
        </v-col>
      </v-row>
    </v-container>
  </template>
  
  <script>
  export default {
    data() {
      return {
        deleteId: "",
        deleteResult: null,
      };
    },
    methods: {
      async deleteUser() {
        try {
          const response = await this.$axios.delete(
            `http://localhost:3000/users/${this.deleteId}`
          );
          this.deleteResult = response.data.message;
        } catch (error) {
          console.error("Error deleting user:", error);
          this.deleteResult = null;

        }

      },
    },
  };
  </script>

  
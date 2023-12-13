<template>
  <v-container>
    <v-row>
      <v-col>
        <v-text>Search User by ID</v-text>

        <v-text-field v-model="searchId" label="Enter User ID"></v-text-field>
        <v-btn @click="searchUser">Search</v-btn>
      </v-col>
    </v-row>

    <v-row>
      <v-col>
        <v-text>Result </v-text>
        <v-row v-if="searchResult">
          <v-col>{{ searchResult.id }}</v-col>
          <v-col>{{ searchResult.name }}</v-col>
          <v-col>{{ searchResult.surname }}</v-col>
          <v-col>{{ searchResult.phone }}</v-col>
          <v-col>{{ searchResult.email }}</v-col>
        </v-row>
        <v-text v-else> No user found</v-text>
      </v-col>
    </v-row>
  </v-container>
</template>
÷
<script>
import axios from "axios";

export default {
  data() {
    return {
      searchId: "",
      searchResult: null,
    };
  },
  methods: {
    async searchUser() {
      try {
        console.log(this.searchId);
        const response = await axios.get(
          `http://localhost:3111/users/${this.searchId}`
        );
        this.searchResult = response.data;
      } catch (error) {
        console.error("Error searching user:", error);
        this.searchResult = null;
      }
    },
  },
};
</script>

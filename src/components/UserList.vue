<template>
  <v-container>
    <v-row>
      <v-col>
        <v-btn @click="sortUsers('asc')">Sort Ascending</v-btn>
        <v-btn @click="sortUsers('desc')">Sort Descending</v-btn>
        <v-btn @click="fetchUsers">Clear Sorting</v-btn>
      </v-col>
    </v-row>

    <v-row>
      <v-col>
        <v-data-table item-key="id">
          <v-row v-for="item in this.users" :key="item.id" >
            <v-col>{{ item.id }}</v-col>
            <v-col>{{ item.name }}</v-col>
            <v-col>{{ item.surname }}</v-col>
            <v-col>{{ item.phone }}</v-col>
            <v-col>{{ item.email }}</v-col>
            <v-col>
              <v-btn @click="deleteUser(item.id)" text> X </v-btn>
            </v-col>
          </v-row>
        </v-data-table>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      users: [],
    };
  },
  mounted() {
    this.fetchUsers();
  },
  methods: {
    async fetchUsers() {
      try {
        const response = await axios.get("http://localhost:3111/users");
        this.users = response.data;
      } catch (error) {
        console.error("Error fetching users:", error);
      }
    },
    async deleteUser(userId) {
      try {
        await axios.delete(`http://localhost:3111/users/${userId}`);
        this.fetchUsers();
      } catch (error) {
        console.error("Error deleting user:", error);
      }
    },
    async sortUsers(sortOrder) {
      try {
        const response = await axios.get(
          `http://localhost:3111/users?sort=${sortOrder}`
        );
        this.users = response.data;
      } catch (error) {
        console.error(`Error sorting users ${sortOrder}:`, error);
      }
    },
  },
};
</script>

<template>
  <v-container>
    <v-row>
      <v-col>
        <div class="title">
          <v-text>Search User by ID</v-text>
        </div>

        <v-text-field v-model="searchId" label="Enter User ID"></v-text-field>
        <v-btn @click="searchUser">Search</v-btn>
      </v-col>
    </v-row>

    <v-row>
      <v-col>
        <v-text>Result </v-text>
        <tr v-if="searchResult">
          <td>{{ searchResult.id }}</td>
          <td>{{ searchResult.name }}</td>
          <td>{{ searchResult.phone }}</td>
          <td>{{ searchResult.email }}</td>
          <td>{{ searchResult.surname }}</td>
        </tr>
        <v-text v-else> No user found</v-text>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
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
        const response = await this.$axios.get(
          `http://localhost:3000/users/${this.searchId}`
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

<style scoped></style>

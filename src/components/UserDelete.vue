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
        await this.$axios.delete(
          `http://localhost:3000/users/${this.deleteId}`
        );
      } catch (error) {
        console.error("Error deleting user:", error);
      }
      window.location.reload();
    },
  },
};
</script>

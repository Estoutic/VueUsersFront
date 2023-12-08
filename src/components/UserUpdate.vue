<template>
  <v-container>
    <v-row>
      <v-col>
        <div class="title">
          <v-text>Update User</v-text>
        </div>
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
    async updateUser() {
      try {
        if (!isNaN(this.userId)) {
          const userId = parseInt(this.userId);

          await this.$axios.put(
            `http://localhost:3000/users/${userId}`,
            this.updatedUser
          );

        } else {
          console.error("Invalid User ID");
        }
      } catch (error) {
        console.error("Error updating user:", error);
      }
    },
  },
};
</script>

<style>
v-text {
  font-size: larger;
  font-weight: 700;
  text-align: center;
}
</style>

<template>
  <v-container>
    <v-row>
      <v-col>
        <div class="title">
          <v-text>Update User</v-text>
        </div>
        <v-form @submit.prevent="updateUser">
          <v-text-field v-model="userId" label="User ID"></v-text-field>
          <v-select
            v-model="selectedField"
            :items="fields"
            label="Select Field to Update"
          ></v-select>
          <v-text-field
            v-model="updatedUser[selectedField]"
            label="New Value"
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
      selectedField: "",
      fields: ["name", "phone", "surname", "email"],
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

        await this.$axios.patch(`http://localhost:3000/users/${this.userId}`, {
          field: this.selectedField,
          value: this.updatedUser[this.selectedField],
        });
        window.location.reload();

      } catch (error) {
        console.error("Error updating user:", error);
      }
    },
  },
};
</script>

<style scoped>
v-text {
  font-size: larger;
  font-weight: 700;
  text-align: center;
}
</style>

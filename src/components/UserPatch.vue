<template>
  <v-container>
    <v-row>
      <v-col>
        <v-text>Update User</v-text>
        <v-form @submit.prevent="updateUser">
          <v-text-field v-model="userId" label="User ID"></v-text-field>
          <v-select
            v-model="selectedField"
            :items="fields"
            label="Select Field to Update"
          ></v-select>
          <v-text-field v-model="fieldValue" label="New Value"></v-text-field>
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
      selectedField: "",
      fields: ["name", "phone", "surname", "email"],
      fieldValue: "",
    };
  },
  methods: {
    // обновление юзера в бд 
    async updateUser() {
      try {
        await axios.patch(`http://localhost:3111/users/${this.userId}`, {
          field: this.selectedField,
          value: this.fieldValue,
        });
        window.location.reload();
      } catch (error) {
        console.error("Error updating user:", error);
      }
    },
  },
};
</script>

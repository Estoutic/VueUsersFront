<template>
  <v-container>
    <v-col class="user-col">
      <div class="title">
        <v-text>USERS</v-text>
      </div>

      <tbody>
        <tr v-for="item in users" :key="item.id" class="user-row">
          <td>{{ item.id }}</td>
          <td>{{ item.name }}</td>
          <td>{{ item.phone }}</td>
          <td>{{ item.email }}</td>
          <td>{{ item.surname }}</td>
        </tr>
      </tbody>
    </v-col>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      users: [],
    };
  },
  created() {
    this.fetchUsers();
  },
  methods: {
    async fetchUsers() {
      try {
        const response = await this.$axios.get("http://localhost:3000/users");
        this.users = response.data;
      } catch (error) {
        console.error("Error fetching users:", error);
      }
    },
  },
};
</script>

<style>
tr {
  background-color: #891e1e;
  color: white;
  font-size: large;
  padding: 10px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 10px;
}

.title {
  display: flex;
  justify-content: center
}
.user-row:hover {
  background-color: #620000;
}
.elevation-1 {
  margin-top: 100px;
}
.user-col {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 10px;
  font-weight: 700;
  font-size: large;
}

.v-data-table-header {
  background-color: #2196f3;
  color: white;
}
</style>

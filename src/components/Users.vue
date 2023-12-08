<template>
  <v-container>
    <v-row>
      <v-col>
        <div class="title">
          <v-text>USERS</v-text>
        </div>
        <v-btn @click="sortUsers('asc')">Sort Ascending</v-btn>
        <v-btn @click="sortUsers('desc')">Sort Descending</v-btn>
        <v-btn @click="fetchUsers">Clear Sorting</v-btn>
      </v-col>
    </v-row>

    <v-col class="user-col">
      <tbody>
        <tr v-for="item in users" :key="item.id" class="user-row">
          <td>{{ item.id }}</td>
          <td>{{ item.name }}</td>
          <td>{{ item.surname }}</td>
          <td>{{ item.phone }}</td>
          <td>{{ item.email }}</td>
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
    async sortUsers(sortOrder) {
      console.log(sortOrder);
      try {
        const response = await this.$axios.get(`http://localhost:3000/filter/${sortOrder}`);
        this.users = response.data;
      } catch (error) {
        console.error(`Error sorting users ${sortOrder}:`, error);
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
  justify-content: center;
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

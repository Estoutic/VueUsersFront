<template>
  <v-app class="main">
    <v-main>
      <Users :users="users" />
      <UserById :axios="$axios" />
      <UserCreate :axios="$axios" />
      <UserUpdate :axios="$axios" />
      <UserPatch :axios="$axios" />
      <UserDelete :axios="$axios" @onUserDeleted="fetchUsers" />
    </v-main>
  </v-app>
</template>

<script>
import Users from './components/Users.vue';
import UserById from './components/UserByID.vue';
import UserCreate from './components/UserCreate.vue';
import UserUpdate from './components/UserUpdate.vue';
import UserPatch from './components/UserPatch.vue';
import UserDelete from './components/UserDelete.vue';

export default {
  name: 'App',

  components: {
    Users,
    UserById,
    UserCreate,
    UserUpdate,
    UserPatch,
    UserDelete,
  },

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
        const response = await this.$axios.get('http://localhost:3000/users');
        this.users = response.data;
      } catch (error) {
        console.error('Error fetching users:', error);
      }
    },
  },
};
</script>

<style>
  .main {
    background: #000;
  }
</style>

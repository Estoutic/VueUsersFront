<template>
  <v-app class="main">
    <v-main>
      <Users/>
      <UserById />
      <UserCreate />
      <UserUpdate  />
      <UserPatch />
    </v-main>
  </v-app>
</template>

<script>
import Users from './components/Users.vue';
import UserById from './components/UserByID.vue';
import UserCreate from './components/UserCreate.vue';
import UserUpdate from './components/UserUpdate.vue';
import UserPatch from './components/UserPatch.vue';

export default {
  name: 'App',

  components: {
    Users,
    UserById,
    UserCreate,
    UserUpdate,
    UserPatch,
  },

};
</script>

<style>
  .main {
    background: #000;
  }
</style>

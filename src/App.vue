<template>
  <v-app class="main">
    <v-main>
      <UserList />
      <UserById />
      <UserCreate />
      <UserUpdate />
      <UserPatch />
    </v-main>
  </v-app>
</template>

<script>
import UserList from "./components/UserList.vue";
import UserById from "./components/UserByID.vue";
import UserCreate from "./components/UserCreate.vue";
import UserUpdate from "./components/UserUpdate.vue";
import UserPatch from "./components/UserPatch.vue";

export default {
  name: "App",

  components: {
    UserList,
    UserById,
    UserCreate,
    UserUpdate,
    UserPatch,
  },
};
</script>

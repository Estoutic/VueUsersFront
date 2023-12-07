<template>
  <v-app class="main">
    <v-main>
      <Users/>
      <UserById/>
    </v-main>
  </v-app>
</template>

<script>
import Users from './components/Users.vue'
import UserById from './components/UserByID.vue'


export default {
  name: 'App',

  components: {
    Users,
    UserById,
  },

  data: () => ({
    //
  }),
}
</script>
<style>
    .main{
        background: #000;
    }
</style>
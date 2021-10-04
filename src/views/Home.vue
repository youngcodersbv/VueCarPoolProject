<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <Users />
    <Commutes />
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import Users from '@/components/Users.vue'; // @ is an alias to /src
import Commutes from '@/components/Commutes.vue'; // @ is an alias to /src

export default defineComponent({
  name: 'Home',
  components: {
    Commutes, Users,
  },
});
</script>

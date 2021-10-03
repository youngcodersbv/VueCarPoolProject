<template>
    <table>
        <thead>
            <tr>
                <td>ID</td>
                <td>Name</td>
            </tr>
        </thead>
        <tbody>
            <tr v-for="(user) in users" :key="user.id">
                <td>{{user.id}}</td>
                <td>{{user.name}}</td>
            </tr>
        </tbody>
    </table>
</template>
<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'Users',
  data() {
      return {
        users: [] as any
      }
  },
  methods: {
      getUsers() {
        fetch("http://localhost:8080/json/users")
          .then(res => res.json())
          .then(json => {
              for (const x of json) {
                  this.users.push(x)
              }
          });
      }
  },
  mounted() {
      this.getUsers()
  }
});
</script>
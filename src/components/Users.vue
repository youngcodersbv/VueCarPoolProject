<template><label for="filter">Filter</label>
    <input v-model="filter" @change="getUsers">
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
        users: [] as any,
            filter: ""
      }
  },
  methods: {
      getUsers() {
            let url = 'http://localhost:8080/json/users'
                    + (this.filter ? '?filter=' + this.filter : '');
            console.log(url);
            fetch(url)
          .then(res => res.json())
          .then(json => {
            while(this.users.length) {
                this.users.pop()
            }

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
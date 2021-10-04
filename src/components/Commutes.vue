<template>
    <table>
        <thead>
            <tr>
                <td>ID</td>
                <td>Home</td>
                <td>Work</td>
            </tr>
        </thead>
        <tbody>
            <tr v-for="(commute) in commutes" :key="commute.id">
                <td>{{commute.id}}</td>
                <td>{{commute.home}}</td>
                <td>{{commute.work}}</td>
            </tr>
        </tbody>
    </table>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    name: 'Commutes',
    data() {
        return {
            commutes: [] as any
        }
    },
    methods: {
        getCommutes() {
            fetch('http://localhost:8080/json/commutes')
                .then(res => res.json())
                .then(json => {
                    for (const commute of json) {
                        console.log(commute)
                        this.commutes.push(commute)
                    }
                       
                })
        }
    },
    mounted() {
        this.getCommutes()
    }
})
</script>
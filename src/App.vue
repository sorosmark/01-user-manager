<script setup>
import { ref } from 'vue';
import { onMounted } from 'vue';
import { getUsers } from '../apis/userAPI';

const users = ref([]);

onMounted(async () => {
    users.value = await getUsers();
});
</script>

<template>
    <table class="table table-striped">
        <thead>
            <tr>
                <th>First Name</th>
                <th>Last Name</th>
                <th>Email address</th>
                <th>-</th>
            </tr>
        </thead>

        <tbody>
            <tr v-for="users in users" :key="users.id">
                <td>{{ users.firstName }}</td>
                <td>{{ users.lastName }}</td>
                <td>{{ users.emailAdress }}</td>
                <td>
                    <button class="btn btn-primary">Edit</button>
                    <button class="btn btn-danger">Delete</button>
                </td>
            </tr>
        </tbody>
    </table>
</template>

<style scoped>
</style>

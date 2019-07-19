<template>
    <div>
        <h1>Users</h1>
        <ul>
            <li v-for="user in users" :key="user.id">
                <nuxt-link :to="{ name: 'users-id', params: {id: user.id} }">
                    {{ user.id }} - {{ user.name }}
                </nuxt-link>
            </li>
        </ul>
    </div>
</template>
<script>
    export default {
        mounted () {
            this.$axios.get("https://jsonplaceholder.typicode.com/users")
                .then(res => res.data)
                .then(users => this.users = users);
        },
        data () {
            return {
                users: []
            }
        }
    }
</script>
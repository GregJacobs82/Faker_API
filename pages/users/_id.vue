<template>
    <div>
        <h1>Name: {{ user.name }}</h1>
        <h3>ID: {{ user.id }}</h3>
        <h6>Email: {{ user.email }}</h6>
        <p>
            <pre>{{ user }}</pre>
        </p>
    </div>
</template>
<script>
    export default {
        mounted() {
            this.$axios.get(`https://jsonplaceholder.typicode.com/users/${this.id}`)
                .then(res => res.data)
                .then(user => this.user = user);

            this.$axios.get(`https://jsonplaceholder.typicode.com/posts`)
                .then(res => res.data)
                // .then(console.log);
                .then(posts => {
                    // only for user of id
                    return posts.filter(post => post.userId == this.id)
                })
                .then(posts => this.posts = posts);
        },
        data () {
            return {
                id: this.$route.params.id,
                user: {},
                posts: []
            }
        }
    }
</script>
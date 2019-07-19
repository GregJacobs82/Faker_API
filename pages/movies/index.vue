<template>
    <div>
        <h1>Movies</h1>
        <ul>
            <li>List of movie here...</li>
        </ul>
    </div>
</template>
<script>
    export default {
        mounted () {
            /* 
            this.$axios.get("https://jsonplaceholder.typicode.com/users")
                .then(res => res.data)
                .then(users => this.users = users);
            */

           let axiosHeaders = {
               headers: {
                    'X-RapidAPI-Host': "movie-database-imdb-alternative.p.rapidapi.com",
                    'X-RapidAPI-Key': "c28f862707msh0a145c3312bb62ap1edf9bjsnd21e71012401",
                }
           };

            this.$axios.get("https://movie-database-imdb-alternative.p.rapidapi.com", axiosHeaders)
                .then(function (result) {
                    console.log(result.status, result.headers, result.body);
                });

        },
        data () {
            return {
                users: []
            }
        }
    }
</script>
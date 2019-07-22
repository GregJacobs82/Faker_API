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
            /* FAKER DATA:
            this.$axios.get("https://jsonplaceholder.typicode.com/users")
                .then(res => res.data)
                .then(users => this.users = users);
            */


           /* IMDB DATA:
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
            */

            /* MOVE QUOTES: (needs authorization with token api key) */
            this.$axios.get("http://movie-quotes-app.herokuapp.com/api/")
                .then(res => res.data)
                .then(function(res) {
                    console.log(res);
                })
                .then(quotes => this.quotes = quotes)
        

        },
        data () {
            return {
                users: [],
                quotes: []
            }
        }
    }
</script>
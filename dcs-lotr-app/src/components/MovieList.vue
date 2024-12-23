<template>
    <div>
        <h3 v-for="movie in movies" :key="movie._id">{{ movie.name }}</h3>
    </div>
</template>

<script>
import LotrService from '../services/LotrService'

export default {
    name: 'MovieList',
    data () {
        return {
            movies:[]
        }
    },
    created () {
        LotrService.getMovies()
        .then ((response) => {
            this.movies = response.data.docs;
        })
        .catch((error) => {
                console.error('Error fetching movies:', error);
        });
    }
}
</script>
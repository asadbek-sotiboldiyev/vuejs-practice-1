<template>
    <div class="block-panel">
        <h1>Kinolar:</h1>
        <div class="movie-list">
            <MovieListItem 
                v-for = "movie in movies" 
                v-bind:movie = "movie"/>
        </div>
    </div>
</template>

<script>
import MovieListItem from '../movie-list-item/MovieListItem.vue';

export default {
    components: {
        MovieListItem
    },
    data() {
        return {
            movies: [
                { name: 'Terminator', views: 811 },
                { name: 'Kelajakka qaytib', views: 900 },
                { name: 'Qasoskorlar', views: 789 },
            ]
        }
    }
};
</script>

<style></style>
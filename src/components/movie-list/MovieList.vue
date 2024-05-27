<template>
    <div class="block-panel">
        <h1>Kinolar:</h1>
        <div class="movie-list">
            <MovieListItem 
                v-for="movie in movies" 
                :key="movie.id"
                v-bind:movie="movie"
                @onToggle="$emit('onToggle', $event)"
            />
        </div>
    </div>
</template>

<script>
import MovieListItem from '../movie-list-item/MovieListItem.vue';

export default {
    components: {
        MovieListItem
    },
    props:{
        movies:{
            type: Array,
            required: true
        },
    },
    methods: {}
};
</script>

<style></style>
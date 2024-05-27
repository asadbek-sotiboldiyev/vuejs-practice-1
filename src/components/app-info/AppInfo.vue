<template>
    <div class="block-panel">
        <h2>Barcha kinolar: {{ allMoviesCount }}</h2>
        <h2>Ko'rilgan kinolar: {{ favouriteMoviesCount }}</h2>
    </div>
</template>

<script>
export default {
    props: {
        allMoviesCount: {
            type: Number,
            required: true
        },
        favouriteMoviesCount: {
            type: Number,
            required: true
        },
    }
};
</script>

<style scoped>
</style>
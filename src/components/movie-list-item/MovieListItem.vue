<template>
    <div class="list-group-item d-flex justify-content-between"
        :class="[{ like: movie.like }, { favourite: movie.favourite }]" >
        <span class="list-group-item-label">
            {{ movie.name }}
        </span>

        <input type="number" class="list-group-input" v-bind:value="movie.views">

        <div class="d-flex justify-content-center align-items-center">
            <button class="btn btn-sm btn-cookie" @click="$emit('onToggle', {id: movie.id, prop: 'favourite'})">
                <i class="fas fa-heart"></i>
            </button>

            <button class="btn btn-sm btn-trash">
                <i class="fas fa-trash"></i>
            </button>

            <button class="btn btn-sm btn-star" @click="$emit('onToggle', {id: movie.id, prop: 'like'})">
                <i class="fas fa-star"></i>
            </button>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        movie: {
            type: Object,
            required: true,
        }
    },
    methods: {
        onLike() {
            this.$emit('onLike', this.movie.id);
        },
        onFavourite(){
            this.$emit('onFavourite', this.movie.id);
        }
    }
}
</script>

<style scoped>
.list-group-item {
    background-color: white;
    font-size: 20px;
    padding: 10px;
    border-bottom: 2px solid grey;
    cursor: pointer;
}

.list-group-item:last-child {
    border: none;
}

.list-group-item span {
    font-size: 22px;
    width: 500px;
}

.list-group-input {
    width: 100px;
    border: none;
    text-align: right;
}

.list-group-item button {
    margin: 0 2px;
    font-size: 17px;
}

.list-group-item .btn-cookie {
    color: coral;
}

.list-group-item .btn-trash {
    color: rgb(219, 3, 3);
}

.list-group-item .btn-star {
    color: rgb(255, 196, 0);
    transition: 0.2s;
}

.list-group-item.like .btn-star {
    color: white;
    background-color: rgb(255, 196, 0);
}

.list-group-item.favourite .list-group-item-label,
.list-group-item.favourite .list-group-input {
    color: #ff8800;
}

.list-group-item.favourite .btn-cookie{
    background-color: #ff8800;
    color: white;
}
</style>
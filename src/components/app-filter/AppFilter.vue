<template>
    <div class="btn-group">
        <button 
            class="btn" 
            @click="filterHandler('all')"
            :class="[(filter == 'all' ? 'btn-dark' : 'btn-outline-dark')]"
        >Barcha kinolar</button>
        <button 
            class="btn" 
            @click="filterHandler('popular')"
            :class="[(filter == 'popular' ? 'btn-dark' : 'btn-outline-dark')]"
        >Sevimli</button>
        <button 
            class="btn"
            @click="filterHandler('mostViews')"
            :class="[(filter == 'mostViews' ? 'btn-dark' : 'btn-outline-dark')]"
        >Ko'p ko'rilgan</button>
    </div>
</template>

<script>
export default {
    props: {
        changeFilterHandler: {
            type: Function,
            required: true
        }
    },
    data(){
        return {
            filter: "all",
        }
    },
    methods: {
        filterHandler(filter) {
            this.filter = filter;
            this.changeFilterHandler(this.filter);
        }
    }
};
</script>

<style>
</style>
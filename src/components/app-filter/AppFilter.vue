<template>
    <div class="btn-group">
        <PrimaryButton v-for="btn in filterButtons" :key="btn.name"
            :class="[(filter == btn.name ? 'btn-dark' : 'btn-outline-dark')]"
            @click="filterHandler(btn.name)"
        >{{ btn.title }}</PrimaryButton>
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
            filterButtons: [
                {title: "Barcha kinolar", name: 'all'},
                {title: "Sevimli", name: 'popular'},
                {title: "Ko'p ko'rilgan", name: 'mostViews'},
            ],
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
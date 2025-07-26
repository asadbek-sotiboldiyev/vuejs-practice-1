<template>
    <input 
        class="my-3 form-control search-input" 
        type="text" 
        placeholder="Kino qidiring"
        @input="changeHandler"
        :value="term"
    >
</template>

<script>
export default {
    props: {
        updateTermHandler: {
            type: Function,
            required: true
        }
    },
    data(){
        return {
            term: ''
        }
    },
    methods: {
        changeHandler(e){
            this.term = e.target.value;
            this.updateTermHandler(this.term);
        }
    },
};
</script>

<style scoped>
.search-input{
    font-size: 25px;
    border: 2px solid wheat;
}
.search-input:focus{
    box-shadow: none;
    border-color: sandybrown;
}
</style>
<template>
    <input type="text" class="form-control"
        :value="modelValue"
        @input="updateInput"
    />
</template>

<script>
export default {
    name: 'InputUi',
    props: {
        modelValue: [String, Number]
    },
    methods: {
        updateInput(e){
            this.$emit('update:modelValue', e.target.value)
        }
    }
}
</script>

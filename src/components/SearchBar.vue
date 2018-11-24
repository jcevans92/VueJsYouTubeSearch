<template>
    <div>
        <!--<input v-on:input="onTextInput" />-->
        <input @input="onTextInput" />
    </div>
</template>

<script>
export default {
    name: 'SearchBar',
    methods: {
        onTextInput(event) {
            this.$emit('termChange', event.target.value);
        }
    }
};
</script>

<style>
</style>
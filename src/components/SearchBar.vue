<template>
    <div>
        <!--<input v-on:input="onTextInput" /> v-on = @-->
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

<style scoped>
input {
    width:75%;
}

div {
    text-align:center;
    margin:20px;
}
</style>
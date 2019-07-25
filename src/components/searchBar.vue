<template>
    <div>
        <!-- <input v-on:input="onInput" /> -->
        <!-- same thing as below -->
        <input @input="onInput" />
    </div>
</template>

<script>
    export default {
        name: "SearchBar",
        //methods give us an opportunity to change data
        methods: {
            onInput: function(event){
                //emit event to parent and pass the value of the input
                this.$emit('termChange', event.target.value);
            }
        }
    }
</script>

<style>
</style>

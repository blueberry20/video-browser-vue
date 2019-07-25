<template>
    <div>
        <div class="input-wrapper">
            <label for="firstName">Name</label>
            <input id="firstName" type="text" aria-describedby="first-name-error" />
        </div>
        <div class="feedback">
            <div id="first-name-error" class="validation-message" aria-live="polite" v-bind:error="{}">
                Please enter a valid name.
            </div>
        </div>
    </div>

</template>

<script>
    export default {
        data(){
            return {
                firstName: ""
                
            }
        },
        methods: {
            validateField(field){
                if (field.length > 2){
                    return true
                }
                else {
                    return false
                }
            }
        }
    }

</script>

<style>

</style>
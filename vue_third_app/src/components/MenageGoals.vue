<template>
    <div>
        <h2>Menage Goals</h2>
        <input type="text" ref="goal">
        <button @click="setGoals">Set Goal</button>
        <ErrorAlert v-if="inputIsInvalid">
            <h2>Input is Invalid!</h2>
            <p>Please enter at least a few characters...</p>
            <button @click="confirmedButton">Okay!</button>
        </ErrorAlert>
    </div>
</template>

<script>
import ErrorAlert from './ErrorAlert.vue';

 export default {
    components: {
        ErrorAlert
    },
    data() {
        return {
            inputIsInvalid: false,
        }
    },
    methods: {
        setGoals() {
            const enteredValue = this.$refs.goal.value;
            if (enteredValue === '') {
                this.inputIsInvalid = true;
            }
        },
        confirmedButton(){
            this.inputIsInvalid = false;
        }
    },
 }
</script>

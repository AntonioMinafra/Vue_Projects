<template>
    <ul>
        <li :class="{active: activeOption === 'poor'}"><button type="button" @click="activate('poor')">Poor</button></li>
        <li :class="{active: activeOption === 'avarage'}"><button type="button" @click="activate('avarage')">Average</button></li>
        <li :class="{active: activeOption === 'great'}"><button type="button" @click="activate('great')">Great</button></li>
    </ul>
</template>

<script>
export default {
    data() {
        return {
            activeOption: null,
        }
    },
    methods: {
        activate(option){
            this.activeOption = option
        }
    }
}
</script>

<style scoped>

.active {
    border-color: rgb(152, 2, 152);
}

.active button {
    color: rgb(152, 2, 152);
}
ul{
    list-style: none;
    padding: 0;
    margin:0.5rem 0;
    display: flex;
}
li{
    margin:0 1rem;
    border: 1px solid #ccc;
    padding: 1rem;
    display: flex;
    justify-content: center;
    align-items: center;
}
button {
    font: inherit;
    border: none;
    background-color: transparent;
    cursor: pointer;
}
</style>
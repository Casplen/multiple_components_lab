<template>
    <select name="country-select" id="country-select" v-on:change="handleInput" v-model="selectedCountry">
        <option v-for="(country, index) in countries" :country="country" :key="index" :value="country">
            {{country.name}}
        </option>
    </select>
</template>

<script>
import { eventBus } from '../main.js'

export default {
    name: 'country-select',
    props: ['country', 'countries'],
    data(){
        return {
            selectedCountry: null
        }

    },
    methods: {
        handleInput(){
            eventBus.$emit('country-selected', this.selectedCountry)
        }
    }
}
</script>

<style>
select {
    padding: 5px;
    border: 3px solid rgb(172, 214, 252);
    border-radius: 10px;
    background-color: whitesmoke;
}
</style>
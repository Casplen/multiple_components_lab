<template>
    <select name="country-select" id="country-select" v-on:input="handleInput">
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
    methods: {
        handleInput(event){
            eventBus.$emit('country-selected', event.target.value)
        }
    }
}
</script>

<style>

</style>
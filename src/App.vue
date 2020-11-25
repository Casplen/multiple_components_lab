<template>
  <div>
    <header>
      <h1>Country List</h1>
    </header>
    <div id="main-container">
      <label for="country-select">Select a Country: </label>
      <country-select :countries="countries"></country-select>
      <br>
      <country-detail :country='selectedCountry'></country-detail>
    </div>
  </div>
</template>

<script>
import CountrySelect from './components/CountrySelect.vue';
import CountryDetail from './components/CountryDetail.vue';
import { eventBus } from './main.js';

export default {
  name: 'app',
  data(){
    return {
      countries: [],
      selectedCountry: null,
    };
  },
  mounted(){
    fetch("https://restcountries.eu/rest/v2/all")
    .then(response => response.json() )
    .then(data => this.countries = data)

    eventBus.$on('country-selected', (country) => {
      console.log('within $on', country)
    })
  },
  components: {
    "country-select": CountrySelect,
    "country-detail": CountryDetail
  }
}
</script>

<style>

</style>
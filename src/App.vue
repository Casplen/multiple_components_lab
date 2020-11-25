<template>
  <div>
    <header>
      <h1>Country List</h1>
    </header>
    <div id="select-container">
      <label for="country-select">Select a Country: </label>
      <country-select :countries="countries"></country-select>
    </div>
    <country-detail v-if="selectedCountry" :country='selectedCountry'></country-detail>
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
      this.selectedCountry = country
    })
  },
  components: {
    "country-select": CountrySelect,
    "country-detail": CountryDetail
  }
}
</script>

<style>
div {
  font-family: 'Roboto', sans-serif;
}

header {
  background-color: rgb(172, 214, 252);
  color: white;
  padding: 10px;
}

#select-container {
  background-color: rgb(228, 228, 228);
  padding:10px;
}

</style>
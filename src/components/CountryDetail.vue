<template>
  <article>
      <p class="country-label">Country: </p>
      <p class="info-box">{{ country.name}} </p>

      <p class="country-label">Region: </p>
      <p class="info-box">{{ country.region}} </p>

      <p class="country-label">Capital: </p>
      <p class="info-box">{{ country.capital}} </p>

      <p class="country-label">Population: </p>
      <p class="info-box">{{ country.population}} </p>
      <br>
      <p class="flag-label">Flag: </p>
      <div class="info-box"><img :src="country.flag" class="flag"></div>
  </article>
</template>

<script>
export default {
    name: 'country-detail',
    props: [ 'country' ]
}
</script>

<style scoped>
article {
    margin: 20px;
    display: grid;
    grid-template-columns: 100px 0.95fr;
    column-gap: 10px;
}

.country-label {
    grid-column: 1/2;
    text-align: right;
    margin: auto 0px;
}

.flag-label {
    grid-column: 1/2;
    text-align: right;
    margin: 10px 0px;
}

.info-box {
    grid-column: 2/3;
    border: 1px solid grey;
    background-color: aliceblue;
    padding: 10px;
}

.flag {
    width: 40%;
}
</style>
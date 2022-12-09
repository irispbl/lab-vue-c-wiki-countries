<template>
  <div class="col-7">
    <img
      :src="
        'https://www.geonames.org/flags/x/' +
        showCountry.alpha2Code.toLowerCase() +
        '.gif'
      "
      alt="country flag"
      style="width: 300px"
    />
    <h1>{{ showCountry.name.common }}</h1>
    <table class="table">
      <thead></thead>
      <tbody>
        <tr>
          <td style="width: 30%">Capital</td>
          <td>{{ showCountry.capital[0] }}</td>
        </tr>
        <tr>
          <td>Area</td>
          <td>{{ showCountry.area }} km <sup>2</sup></td>
        </tr>
        <tr>
          <td>Borders</td>
          <td>
            <ul v-for="(country, index) in showCountry.borders" :key="index">
              <li>
                <router-link :to="`/${showCountry.alpha3Code}`">{{country}}</router-link>
              </li>
            </ul>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
<script>
import countries from "../assets/countries.json";

export default {
  data() {
    return {
      countries: countries,
    };
  },
  computed: {
    showCountry() {
      const countryId = this.$route.params.alpha3Code;
      return this.countries.find(function (country) {
        if (country.alpha3Code === countryId) {
          return true;
        } else {
          return false;
        }
      });
    },
  },
};
</script>

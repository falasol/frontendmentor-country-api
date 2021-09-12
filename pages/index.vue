<template>
  <fragment>
    <Header @changeTheme="changeTheme" />
    <main>
      <div class="feature"><Search @setQuery="setQuery" /><Dropdown @filterByRegion="filterByRegion" /></div>
      <div class="country-wrapper">
        <CountryCard v-for="country in filteredCountries" :key="country.id" :country="country"/>      
      </div>
    </main>
  </fragment>
</template>

<script>
import Header from "../components/Header.vue"
import Search from "../components/Search.vue"
import Dropdown from "../components/Dropdown.vue"
import CountryCard from "../components/CountryCard.vue"

export default {
  data() {
    return {
      countries: [],
      filter: "",
      query: "",
      theme: "light",
    }
  },
  components: {
    Header, Search, Dropdown, CountryCard
  },
  async fetch() {
    const result = await fetch(
      'https://restcountries.eu/rest/v2/all'
    ).then(
      res => res.json()
    )
    for(let i=0; i<result.length; i++){
      this.countries.push(
        {
          id: i,
          name: result[i].name,
          population: result[i].population,
          region: result[i].region,
          capital: result[i].capital,
          flag: result[i].flag,
          alphaCode: result[i].alpha3Code
        }
      );
    }
  },
  methods: {
    filterByRegion(region){
      if(region == "All"){
        this.filter = "";
      }else{
        this.filter = region;
      }
    },
    setQuery(query){
      this.query = query;
    },
    changeTheme(){
      console.log("change");
      if(this.theme == "light"){
        this.theme = "dark";
        document.documentElement.style.setProperty('--background', 'hsl(207, 26%, 17%)');
      }else{
        this.theme = "light";
      }
    },
  },
  computed : {
    filteredCountries(){            
      let returnedCountries = this.countries;
      if(this.filter){
        returnedCountries = returnedCountries.filter(country => country.region == this.filter);
      }
      if(this.query){
        returnedCountries = returnedCountries.filter(country => country.name.toLowerCase().includes(this.query.toLowerCase()));
      }
      return returnedCountries;
    }
  }
}
</script>

<style scoped>
  .feature{
    margin-top: 30px;
    padding: 0 2%;
    display: flex;
    justify-content: space-between;
  }
  .country-wrapper{
    margin-top: 30px;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    padding: 0px 2%;
  }

  @media (min-width:521px) {
    .country-wrapper{
      justify-content: space-between;
    }
  }

  @media (min-width:728px) {
    .feature{
      padding: 0 10%;
    }
    .country-wrapper{
      padding: 0 10%;
    }
  }
</style>
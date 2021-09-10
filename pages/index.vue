<template>
  <fragment>
    <Header/>
    <div class="feature"><Search /><Dropdown /></div>
    <div class="country-wrapper">
      <CountryCard />
      <CountryCard />
      <CountryCard />
      <CountryCard />  
      <CountryCard />
      <CountryCard />
      <CountryCard />
      <CountryCard />
    </div>
  </fragment>
</template>

<script>
import Header from "../components/Header.vue"
import Search from "../components/Search.vue"
import Dropdown from "../components/Dropdown.vue"
import CountryCard from "../components/CountryCard.vue"

export default {
  components: {
    Header, Search, Dropdown, CountryCard
  }
}
</script>

<style scoped>
  .feature{
    margin-top: 30px;
    padding: 0 10%;
    display: flex;
    justify-content: space-between;

  }
  .country-wrapper{
    margin-top: 30px;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    padding: 0px 10%;
  }
</style>
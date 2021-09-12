<template>
    <a :href="'/country/' + country.alphaCode.toLowerCase()">
        <div class="country-card">
            <div class="flag-wrapper">
                <img class="flag" :src="country.flag"/>
            </div>        
            <div class="country-intro">
                <h3>{{ country.name }}</h3>
                <div class="country-detail">
                    <p>Population: <span>{{ country.population.toLocaleString() }}</span></p>
                    <p>Region: <span>{{ country.region }}</span></p>
                    <p>Capital: <span>{{ country.capital }}</span></p>
                </div>
            </div>
        </div>
    </a>
</template>

<script>
export default {
    props: {
        country: Object,
    }
}
</script>


<style scoped>
    .country-card{
        width: 250px;
        border: 1px solid #DCDCDC;
        margin-bottom: 30px;
        border-radius: 5px;
        background-color: var(--elements);
    }

    .flag{
        width: 100%;
        border-top-right-radius: 3px;
        border-top-left-radius: 3px;
    }

    .flag-wrapper{
        min-height: 200px;
    }

    .country-intro{
        padding: 10px 10px 30px 10px;
    }

    p{
        margin: 0;
        font-weight: 600;
    }

    span{
        font-weight: normal;
    }
    p:not(:last-child){
        margin-bottom: 3px;
    }
</style>
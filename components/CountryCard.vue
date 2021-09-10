<template>
    <div class="country-card">
        <img class="flag" src="https://restcountries.eu/data/afg.svg"/>
        <div class="country-intro">
            <h3>Brazil</h3>
            <div class="country-detail">
                <p>Population:<span>23,412,123</span></p>
                <p>Region:<span>Americas</span></p>
                <p>Capital:<span>Brasilia</span></p>
            </div>
        </div>
    </div>
</template>


<style scoped>
    .country-card{
        width: 250px;
        border: 1px solid var(--input);
        margin-bottom: 30px;
        border-radius: 5px;
    }

    .flag{
        width: 100%;
    }

    .country-intro{
        padding: 10px 10px 30px 10px;
    }

    p{
        margin: 0;
    }

    p:not(:last-child){
        margin-bottom: 3px;
    }
</style>
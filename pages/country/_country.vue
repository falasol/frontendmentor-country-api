<template>
  <fragment>
    <Header/>
    <main>
        <div class="feature-row"><Button text="← Back" destination="" /></div>    
        <div class="content">
            <img :src="countryInfo.flag" >
            <div class="data">
                <h2> {{ countryInfo.name }} </h2>
                <div class="intro">
                    <div class="intro1">
                        <p>Native Name: <span>{{ countryInfo.nativeName }}</span></p>
                        <p>Population: <span>{{ countryInfo.population.toLocaleString() }}</span></p>
                        <p>Region: <span>{{ countryInfo.region }}</span></p>
                        <p>Sub Region: <span>{{ countryInfo.subRegion }}</span></p>
                        <p>Capital: <span>{{ countryInfo.capital }}</span></p>
                    </div>
                    <div class="intro2">
                        <p>Top Level Domain: <span>{{ countryInfo.topLevelDomain[0] }}</span></p>
                        <p>Currencies: <span>{{ printCurrencies(countryInfo.currencies) }}</span></p>                
                        <p>Languages: <span>{{ printLanguages(countryInfo.languages) }}</span></p>
                    </div>            
                </div>    
                <div class="borderCountries">
                    <h3>Border Countries:</h3>
                    <div class="border-wrapper">
                        <Button v-for="border in borders" :key="border.code" :text="borde.name" class="btn" :destination="'country/' + border.code.toLowerCase()"> </Button>
                    </div>                    
                </div>
            </div>                    
            
        </div>        
    </main>
  </fragment>
</template>

<script>
import Button from "../../components/Button.vue";

export default {
    async asyncData({ params }) {      
        const slug = params.country // When calling /abc the slug will be "abc"
        const result = await fetch(
            "https://restcountries.eu/rest/v2/alpha/" + slug
        ).then(
            res => res.json()
        )
        const countryInfo = result;        
        return { slug, countryInfo }
    },
    data(){
        return {
            countryInfo: {},
            borders:[]
        }
    },
    // async fetch(){
    //     const result = await fetch(
    //         "https://restcountries.eu/rest/v2/alpha/" + this.slug
    //     ).then(
    //         res => res.json()
    //     )
    //     this.countryInfo = result;

    //     result.borders.forEach(border => {
    //         console.log(border);
    //         const countryName = fetch(
    //            "https://restcountries.eu/rest/v2/alpha/" + border
    //         ).then(
    //             res => res.json()
    //         );
    //         console.log("hello");
    //         console.log("00", countryName.name);

    //         this.borders.push(
    //             {
    //                 code: border, 
    //                 name: countryName.name,
    //             }
    //         );            
    //     });
    //     console.log("11", this.borders);
    //     console.log(this.countryInfo);
    // },
    

    methods: {
        printLanguages(languages){
            let text = "";
            for(let i=0; i<languages.length-1; i++){
                text += languages[i].name + ", "
            }
            text += languages[languages.length - 1].name;
            return text;
        },
        printCurrencies(currencies){
            let text = "";
            for(let i=0; i<currencies.length-1; i++){
                text += currencies[i].name + ", "
            }
            text += currencies[currencies.length - 1].name;
            return text;
        },
        async getCountryFullName(code){
            const name = await fetch(
                "https://restcountries.eu/rest/v2/alpha/" + code
            ).then(
                res => res.json().name
            ) 
            return "hello";           
        },        
    },
   
    components: {
        Button, 
    }
}
</script>

<style scoped>
    .feature-row{
        margin-top: 40px;
        padding: 0 5%;
        margin-bottom: 50px;
    }
    img{
        margin-top: 80px;
        text-align: center;
        width: 100%;
        margin: auto;
        max-width: 350px;
    }
    .content{
        padding: 0 5%;
        color: var(--text);
    }

    .content p{
        font-weight: 600;
        margin: 0;
        line-height: 2;
    }
    .content span{
        font-weight: 400;
    }

    .intro1 {
        margin-bottom: 40px;
    }

    .btn{
        margin-bottom: 10px;
    }

    .btn:not(:last-child){
        margin-right: 20px;
    }

    .border-wrapper{
        display: flex;
        flex-wrap: wrap;
    }

    @media (min-width: 900px) {
        .feature-row{
            padding: 0 10%;
        }
        .content{
            display: flex;
            padding: 0 10%;            
        }

        .intro{
            display: flex;
        }

        .intro1{
            margin-right: 30%;
            
        }
        img{
            margin: 0;
            width: 40%;
            max-width: none;
            height: auto;
            object-fit: contain;
        }
        .data{
            margin-left: 100px;
            width: 60%;
        }
    }

    @media (min-width: 1440px) {
        .intro1{
            margin-right: 30%;
            width: 40%;
        }
    }
</style>
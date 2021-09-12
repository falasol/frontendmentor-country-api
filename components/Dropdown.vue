<template>
    <form>
        <div class="filter-bar" @click="changeOptionsIsOpened">
            <span>{{selectedOption}}</span>
            <font-awesome-icon :icon="['fas', 'chevron-down']" class="icon"/>
        </div>

        <div class="options" v-show="optionsIsOpened">
            <ul>
                <li @click="selectOption">Africa</li>
                <li @click="selectOption">Americas</li>
                <li @click="selectOption">Asia</li>
                <li @click="selectOption">Europe</li>
                <li @click="selectOption">Oceania</li>
                <li @click="selectOption">All</li>
            </ul>
        </div>

        
    </form>
</template>
<script>
export default {
    data(){
        return {
            optionsIsOpened: false,
            selectedOption: "Filter by Region",
        }
    },
    methods: {
        changeOptionsIsOpened(){            
            this.optionsIsOpened = !this.optionsIsOpened;
        },
        selectOption(event){
            if(event.target.innerText == "All"){
                this.selectedOption = "Filter by Region";    
            }else{
                this.selectedOption = event.target.innerText;
            }            
            this.optionsIsOpened = !this.optionsIsOpened;
            this.$emit("filterByRegion", event.target.innerText);
        }
    },
}
</script>

<style scoped>
    .filter-bar{
        border: 1px solid #CCC;
        padding: 10px 20px;
        border-radius: 5px;
        background-color: var(--elements);
        width: 200px;
        display: flex;
        justify-content: space-between;
        align-items: center;

    }

    span{
        margin-right: 20px;
        color: var(--text);
    }

    .icon{
        color: var(--input);
    }

    input{
        border: none;
        font-size: 16px;
        color: var(--input);
        font-family: "Nunito Sans", sans-serif;
    }

    input::placeholder{
         font-family: "Nunito Sans", sans-serif;
    }

    .options{
        position: absolute;
        border: 1px solid #CCC;
        border-radius: 5px;
        background-color: var(--elements);
        width: 200px;
        margin-top: 1px;
    }

    .options ul{
        margin:0;
        padding:0;
        list-style:none
    }

    .options li{
        padding: 10px 20px;
        color: var(--text);
    }

    .options li:hover{
        background-color: #dcdcdc;
    }

</style>
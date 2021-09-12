<template>
    <form>
        <div class="search-bar">
            <font-awesome-icon :icon="['fas', 'search']" class="icon"/>
            <input type="text" placeholder="Search for a country..." v-model="query" />
        </div>
    </form>
</template>

<script>
export default {    
    data(){
        return {
            query: "",
        }
    },
    watch: {
        query(){
            clearTimeout(this.queryTimeout);
            this.queryTimeout = setTimeout(() => {
                this.$emit("setQuery", this.query);    
            }, 500);            
        }
    },
}
</script>

<style scoped>
    .search-bar{
        width: 250px;        
        border: 1px solid #CCC;
        padding: 10px 20px;
        border-radius: 5px;
        background-color: var(--elements);
    }

    .icon{
        margin-right: 10px;
        color: var(--input);
    }

    input{
        border: none;
        font-size: 16px;
        color: var(--input);
        font-family: "Nunito Sans", sans-serif;
        background-color: var(--element);
    }

    input::placeholder{
         font-family: "Nunito Sans", sans-serif;
    }

    @media (min-width: 728px) {
        .search-bar{
            width: 300px;
        }
    }
</style>
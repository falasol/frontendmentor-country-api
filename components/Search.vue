<template>
    <form>
        <div class="search-bar">
            <font-awesome-icon :icon="['fas', 'search']" class="icon"/>
            <input type="text" placeholder="Search for a country..."/>
        </div>
    </form>
</template>

<style scoped>
    .search-bar{
        width: 300px;        
        border: 1px solid #CCC;
        padding: 10px 20px;
        border-radius: 5px;
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
    }

    input::placeholder{
         font-family: "Nunito Sans", sans-serif;
    }
</style>
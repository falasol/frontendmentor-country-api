<template>
    <header>
        <nuxt-link to="/" class="logo">Where in the world?</nuxt-link>
        <div class="mode-switcher" @click="changeTheme">        
            <font-awesome-icon v-if="$colorMode.value == 'dark'" :icon="['fas', 'sun']" class="icon"/>
            <font-awesome-icon v-else :icon="['fas', 'moon']" class="icon"/>
            <p v-if="$colorMode.value == 'dark'">Light Mode</p>
            <p v-if="$colorMode.value == 'light'">Dark Mode</p>
        </div>
    </header>
</template>

<script>
export default {    
    methods:{
        changeTheme(){            
            if(this.$colorMode.value == "light"){
                this.$colorMode.preference = "dark";
            }else{
                this.$colorMode.preference = "light";
            }            
        },        
    },    
}
</script>

<style scoped>
    header{
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 0px 3%;
        box-shadow: 0px 2px 4px #CCC;
        background-color: var(--elements);
    }
    p{
        color: var(--text);        
    }
    .logo{
        font-weight: 600;
    }
    .mode-switcher{
        display: flex;
        align-items: center;
    }
    .mode-switcher:hover{
        cursor: pointer;
    }
    .icon{
        margin-right: 10px;
        color: var(--text);
    }

    @media (min-width: 728px) {
        header{
            padding: 0px 10%;
        }
    }
</style>
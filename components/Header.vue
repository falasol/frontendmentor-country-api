<template>
    <header>
        <p class="logo">Where in the world?</p>
        <div class="mode-switcher">        
            <font-awesome-icon :icon="['fas', 'moon']" class="icon"/>
            <p>Dark Mode</p>
        </div>
    </header>
</template>

<style scoped>
    header{
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 0px 10%;
        box-shadow: 0px 2px 4px #CCC;
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
    .icon{
        margin-right: 10px;
    }
</style>
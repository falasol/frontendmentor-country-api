<template>
    <a :href="'/'+destination" class="button">{{text}}</a>
</template>

<script>
export default {
    props: {
        text: String,
        destination: String, 
    }
}
</script>

<style scoped>
    .button{
        background-color: var(--elements);
        padding: 5px 30px;
        border: 1px solid rgb(219, 219, 219, 0.8);
        box-shadow: 0 0 10px rgb(219, 219, 219, 0.8);
    }
</style>
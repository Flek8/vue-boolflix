<template>
    <main>
        <MyCard v-for="(film,index) in listaFilms" 
                :key="index"
                :film="film"/>
    </main>
</template>

<script>
import MyCard from './partials/MyCard.vue';

export default {
    name: 'MyMain',
    components: {
        MyCard
    },
    props: {
        listaFilms: Array
    }
}
</script>

<style scoped lang="scss">
    main {
        padding: 20px;
        background-color: rgb(100, 100, 100);
        display: flex;
        flex-wrap: wrap;
    }
</style>
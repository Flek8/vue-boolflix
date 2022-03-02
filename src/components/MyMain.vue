<template>
    <main>
        <h2>Film</h2>
        <ListaFilms :films="listaFilms"/>
        <h2>Serie TV</h2>
        <ListaSerie :series="listaSerie"/>
    </main>
</template>

<script>
import ListaFilms from './ListaFilms.vue';
import ListaSerie from './ListaSerie.vue'

export default {
    name: 'MyMain',
    components: {
        ListaFilms,
        ListaSerie
    },
    props: {
        listaFilms: Array,
        listaSerie: Array
    }
}
</script>

<style scoped lang="scss">
    main {
        padding: 20px;
        background-color: rgb(100, 100, 100);

        h2 {
            color: white;
        }
    }
</style>
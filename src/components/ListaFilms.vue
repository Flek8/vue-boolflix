<template>
  <section>
      <FilmCard v-for="(film,index) in films" 
                :key="index"
                :film="film"/>
  </section>
</template>

<script>

import FilmCard from './partials/FilmCard.vue';

export default {
    name: 'ListaFilms',
    components: {
        FilmCard
    },
    props: {
        'films': Array
    }
}
</script>

<style scoped lang="scss">
    section {
        display: flex;
        flex-wrap: wrap;
    }
</style>
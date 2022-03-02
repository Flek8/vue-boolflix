<template>
  <section>
    <SerieCard v-for="(serie,index) in series" 
                :key="index"
                :serie="serie"/>
  </section>
</template>

<script>

import SerieCard from './partials/SerieCard.vue';

export default {
    name: 'ListaSerie',
    components: {
        SerieCard
    },
    props: {
      'series': Array
    }
}
</script>

<style scoped lang="scss">
    section {
        display: flex;
        flex-wrap: wrap;
    }
</style>
<template>

  <div class="card">
      <h2>{{film.title}}</h2>
      <h4>{{film.original_title}}</h4>
      <img :src="require('../../assets/flags/' + film.original_language + '.svg')" alt="">
      <h4>{{film.vote_average}}</h4>
  </div>

</template>

<script>
export default {
    name: 'MyCard',
    props: {
        film: Object
    },
    
}
</script>

<style scoped lang="scss">
    .card {
        
        width: calc((100% - 40px - (20px * 5)) / 5);
        background-color: black;
        margin: 10px;
        color: white;
        padding: 5px;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        text-align: center;

        h4 {
            margin: 7px 0;
        }

        img {
            height: 14px;
        }
    }    
</style>
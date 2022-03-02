<template>

  <div class="card">
        <img class="copertina" :src="'https://image.tmdb.org/t/p/w342/' + film.poster_path">
        <div class="card-info">
            <h2>{{serie.name}}</h2>
            <h4>{{serie.original_name}}</h4>
            <p>{{serie.overview}}</p>
            <img :src="require('../../assets/flags/' + serie.original_language + '.svg')" alt="">
            <h4>{{serie.vote_average}}</h4>
        </div>
  </div>

</template>

<script>
export default {
    name: 'MyCard',
    props: {
        serie: Object
    },
    
}
</script>

<style scoped lang="scss">
    .card {
        
        width: calc((100% - 40px - (20px * 4)) / 4);
        height: 450px;
        background-color: black;
        margin: 10px;
        color: white;
        position: relative;

        &:hover {
            transform: rotateY(180deg);
        }
        &:hover .copertina {
            display: none;
        }
        &:hover .card-info {
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            text-align: center;
        }

        .card-info {
            padding: 5px;
            display: none;
        }

        img.copertina {
            position: absolute;
            width: 100%;
            height: 100%;
            z-index: 99;
        }

        h4 {
            margin: 7px 0;
        }

        img {
            height: 14px;
        }
        
        
    }    
</style>
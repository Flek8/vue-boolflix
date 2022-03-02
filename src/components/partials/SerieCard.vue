<template>
  <div class="card flip-card">
    <div class="flip-card-inner">
        <div class="flip-card-front">
            <img class="copertina" v-if="serie.poster_path" :src="'https://image.tmdb.org/t/p/w342/' + serie.poster_path">
            <img v-else class="fallback" src="../../assets/ciak.jpg">
        </div>
        <div class="flip-card-back">
            <h5>Titolo: </h5><p>{{serie.name}}</p> <br>
            <h5>Titolo Originale: </h5><p>{{serie.original_name}}</p> <br>
            <h5>Trama: </h5><p>{{serie.overview}}</p> <br>
            <img class="flag" :src="require('../../assets/flags/' + serie.original_language + '.svg')" alt=""> <br>
            <h5>Voto: </h5> <i v-for="i in 5" :key="i"  class="fa-star" :class="i < getVoto()? 'fa-solid':'fa-regular'"></i>{{serie.vote_average}}
        </div>
    </div>
  </div>
</template>

<script>
export default {
    name: 'MyCard',
    props: {
        serie: Object
    },
    methods: {
        getVoto() {
            return Math.ceil(this.serie.vote_average / 2)
        }
    }
    
}
</script>

<style scoped lang="scss">
    .flip-card {
        
        width: calc((100% - 40px - (20px * 4)) / 4);
        height: 450px;
        background-color: black;
        margin: 10px;
        color: white;
        perspective: 1000px;

        &:hover .flip-card-inner {
            transform: rotateY(180deg);
        }
        
        .flip-card-inner {
            position: relative;
            width: 100%;
            height: 100%;
            transition: transform 0.8s;
            transform-style: preserve-3d;
        }

        .flip-card-front, .flip-card-back {
            position: absolute;
            width: 100%;
            height: 100%;
            backface-visibility: hidden;
        }

        .flip-card-back {
            padding: 10px;
            transform: rotateY(180deg);
            
        }

        img.copertina {
            width: 100%;
            height: 100%;
        }

        h5 {
            margin: 7px 0;
        }

        img.flag {
            height: 14px;
        }
        p {
            font-size: 12px;
            display: inline-block;
        }
        .fa-star {
            color: gold;
        }
        
    }    
</style>
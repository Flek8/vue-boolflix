<template>

    <div class="card flip-card">
        <div class="flip-card-inner">
            <div class="flip-card-front">
                <img class="copertina" v-if="film.poster_path" :src="'https://image.tmdb.org/t/p/w342/' + film.poster_path">
                <img v-else class="fallback" src="../../assets/ciak.jpg">
            </div>
            <div class="flip-card-back">
                <h5>Titolo: </h5><p> {{film.title}}</p> <br>
                <h5>Titolo Originale: </h5><p> {{film.original_title}}</p> <br>
                <h5>Trama: </h5><p> {{film.overview}}</p> <br>
                <img class="flag" :src="require('../../assets/flags/' + film.original_language + '.svg')" alt=""> <br>
                <h5>Voto: </h5> <i v-for="i in 5" :key="i"  class="fa-star" :class="i < getVoto()? 'fa-solid':'fa-regular'"></i>
            </div>
        </div>
    </div>

</template>

<script>
export default {
    name: 'MyCard',
    props: {
        film: Object
    },
    methods: {
        getVoto() {
            return Math.ceil(this.film.vote_average / 2)
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
            display: inline-block;
            margin: 5px 2px;
        }

        img.flag {
            height: 14px;
            margin: 10px 0;
        }
        img.fallback {
            width: 100%;
            height: 100%;
            object-fit: fill;
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
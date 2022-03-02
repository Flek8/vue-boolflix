<template>

    <div class="card flip-card">
        <div class="flip-card-inner">
            <div class="flip-card-front">
                <img class="copertina" :src="'https://image.tmdb.org/t/p/w342/' + film.poster_path">
            </div>
            <div class="flip-card-back">
                <h4>Titolo: </h4><p> {{film.title}}</p> <br>
                <h4>Titolo Originale: </h4><p> {{film.original_title}}</p> <br>
                <h4>Trama: </h4><p> {{film.overview}}</p> <br>
                <img class="flag" :src="require('../../assets/flags/' + film.original_language + '.svg')" alt=""> <br>
                <h4>Voto: </h4> {{film.vote_average}}
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
    
}
</script>

<style scoped lang="scss">
    .flip-card {
        
        width: calc((100% - 40px - (20px * 4)) / 4);
        height: 450px;
        background-color: black;
        margin: 10px;
        color: white;
        border: 1px solid #f1f1f1;
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

        h4 {
            display: inline-block;
            margin: 5px 2px;
        }

        img.flag {
            height: 14px;
            margin: 10px 0;
        }
        p {
            font-size: 12px;
            display: inline-block;
        }
    }    
</style>
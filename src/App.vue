<template>
  <div id="app">
    <MyHeader @ricerca="riceviRichiesta"/>
    <MyMain :listaFilms="listaFilms" :listaSerie="listaSerie"/>
  </div>
</template>

<script>
import MyHeader from './components/MyHeader.vue';
import MyMain from './components/MyMain.vue';
const axios = require('axios');

export default {
  name: 'App',
  components: {
      MyHeader,
      MyMain
  },
  data() {
    return {
      testoRichiesto: '',
      listaFilms: [],
      listaSerie: []
    }
  },
  methods: {
      riceviRichiesta(testo) {
          this.testoRichiesto = testo;
          console.log(this.testoRichiesto);
          this.getFilms();
          this.getSeries();

      },
      getFilms() {
          // Make a request for a user with a given ID
          axios.get('https://api.themoviedb.org/3/search/movie?api_key=a40dc7dbb98acbc30fa5ed9db217909a&query=' + this.testoRichiesto + '&language=it-IT')
          .then((response) => {
              // handle success
              this.listaFilms = response.data.results;
              console.log(this.listaFilms);
          })
          .catch(function (error) {
              // handle error
              console.log(error);
          })
          .then(function () {
              // always executed
          });
            },
      getSeries() {
          // Make a request for a user with a given ID
          axios.get('https://api.themoviedb.org/3/search/tv?api_key=a40dc7dbb98acbc30fa5ed9db217909a&query=' + this.testoRichiesto + '&language=it-IT')
          .then((response) => {
              // handle success
              this.listaSerie = response.data.results;
              console.log(this.listaSerie);
          })
          .catch(function (error) {
              // handle error
              console.log(error);
          })
          .then(function () {
              // always executed
          });
      }
  }
}
</script>

<style lang="scss">
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: Arial, Helvetica, sans-serif;
    }
</style>

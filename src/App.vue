<template>
  <div id="app">
    
    <header>
      <Header @selectSearch = 'musicGenres' />
    </header>

    <main>
      <Main :listCard="filtermusicGenres"/>
    </main>
  </div>
</template>

<script>

import axios from 'axios';
import Header from "@/components/Header.vue";
import Main from "@/components/Main.vue";

export default {
  name: 'App',
  components: {
    Header,
    Main,
  },
  data(){
    return{
      listDisc: null,
      currentMusicGenres: '',
    }
  },
  computed: {

    filtermusicGenres() {
      if (this.currentMusicGenres == '' || this.currentMusicGenres == 'all') {
        return this.listDisc;
      }

      return this.listDisc.filter(item => {

        return item.genre.toLowerCase().includes(this.currentMusicGenres.toLowerCase())
      })
    }
  },
  created() {

    this.getListDisc();
  },
  methods: {

    getListDisc(){

      axios.get('https://flynn.boolean.careers/exercises/api/array/music')

      .then(result => {

        this.listDisc = result.data.response;
      })
      .catch(error => {
        console.log(error);
      })
    },

    musicGenres(text){
      this.currentMusicGenres = text;
    },
  }
}

</script>

<style lang="scss">
@import '@/style/globals';

  #app{

    min-height: 100vh;
    background-color: #1d2d3c;

    header{
      background-color: #2e3a46;
    }
    main{
      display: flex;
      flex-direction: column;
      height: 100%;
      background-color: #1d2d3c;
      padding-top: 50px;
    }
  }

</style>

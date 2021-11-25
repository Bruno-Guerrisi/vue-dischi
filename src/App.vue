<template>
  <div id="app">
    
    <header>
      <Header />
    </header>

    <main>
      <Main />
    </main>
  </div>
</template>

<script>

import Header from "@/components/Header.vue";
import Main from "@/components/Main.vue";

export default {
  name: 'App',
  components: {
    Header,
    Main,
  },
}
</script>

<style lang="scss">
@import '@/style/globals';

  #app{

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

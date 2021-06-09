<template>
  <div id="app">
    <header>
      <Header/>
    </header>

    <main>
      <div class="container">
        
       <ListaCanzoni/> 

      </div>
    </main>
    
    
  </div>
</template>

<script>
import Header from './components/Header.vue';
import ListaCanzoni from './components/ListaCanzoni.vue';


export default {
  name: 'App',
  components: {
    Header:Header,
    ListaCanzoni:ListaCanzoni,
    
  },
  
}
</script>

<style lang="scss">
  @import '~bootstrap';

  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  body{
    
    background-color: #1e2d3b;
  }

  header{
    display: flex;
    align-items:center;
    height: 80px;
    background-color:#2e3a46 ;
  }




</style>

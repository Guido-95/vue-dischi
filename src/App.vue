<template>
  <div id="app">
    <header>
      <Header/>
      <!-- <div class="select">
        <select name="generi" id="generi">
          <option value="Tutti">Tutti</option>
          <option value="Rock">Rock</option>
          <option value="Pop">Pop</option>
          <option value="Jazz">Jazz</option>
          <option value="Metal">Metal</option>
        </select>
      </div> -->
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
  .select{
    width: 100%;
    text-align: right;
    margin-right: 50px;
  }
  
</style>

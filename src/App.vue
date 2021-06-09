<template>
  <div id="app">
    <header>
      <Header/>
    </header>

    <main>
      <div class="container">
        <div class="row">
          <div class="col-lg-2 col-md-3 col-sm-4">

          </div>
          <div class="col-lg-2 col-md-3 col-sm-4">

          </div>
          <div class="col-lg-2 col-md-3 col-sm-4">

          </div>
          <div class="col-lg-2 col-md-3 col-sm-4">

          </div>
          <div class="col-lg-2 col-md-3 col-sm-4">

          </div>
        </div>
      </div>
    </main>
    
    
  </div>
</template>

<script>
import Header from './components/Header.vue'

export default {
  name: 'App',
  components: {
    Header:Header,

  }
}
</script>

<style lang="scss">
  @import '~bootstrap';

  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  header{
    display: flex;
    align-items:center;
    height: 80px;
    background-color:#2e3a46 ;
  }

  main{
    height: calc(100vh - 80px);
    background-color:#1e2d3b;
  }

  .container{
    height: 100%;
    background-color: chartreuse;
    .row{
      padding: 100px;
      justify-content: center;
      
      div {
      height: 300px;
      border: 1px solid black;
      background-color: yellow;
      }

    }
    
  }


</style>

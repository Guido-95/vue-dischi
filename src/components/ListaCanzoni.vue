<template>
    <div class="container" v-if='caricamento'>
        <div class="canzoni row">
            <Select class="select" :arrayOggettiCanzoni = 'canzoni ' @cambiamentoSelectGenere="trovaGenere"/>

            <Select2 class="select2" :arrayOggettiCanzoni = 'canzoni ' @cambiamentoSelectAutore="trovaAutore"/>

            
            <div class="canzone"  v-for="canzone,indicatore in filtraCanzone" :key="indicatore">

                <Canzone :canzone="canzone"/>
               
            </div>

        </div>
    </div>
    <div v-else class="caricamento">
        
        <div class="caricamento-animato">
            <div class="caricamento2"></div>
        </div>
        <h4>Caricamento in corso..</h4>  
    </div>
</template>

<script>
import Canzone from './Canzone.vue'
import Select from './Select.vue'
import Select2 from './Select2.vue'
import axios from 'axios'
export default {
    name:'ListaCanzoni',
    components:{
        Canzone:Canzone,
        Select:Select,
        Select2:Select2
    },
    data(){
        return{
            canzoni:[],
            caricamento : false,
            genere: 'Tutti',
            autore:'Tutti',
            booleanoGeneri:false,
            booleanoAutori:false,

        }
    },
    methods:{
        trovaGenere(valoreSelect){
            console.log(valoreSelect);
            this.genere = valoreSelect;
            this.autore = 'Tutti'
        },
        trovaAutore(valoreSelect){
            console.log(valoreSelect);
            this.autore = valoreSelect;
            this.genere = 'Tutti'
        }
    },
    computed: {
      
        filtraCanzone(){
            if(this.genere == 'Tutti' && this.autore == 'Tutti'){
                return this.canzoni;
            }else if (this.autore != 'Tutti'){
                return this.canzoni.filter(
                element => element.author == this.autore
            );
            }
            return this.canzoni.filter(
                element => element.genre == this.genere
            );
            }
            
        },
    created(){
        axios.get("https://flynn.boolean.careers/exercises/api/array/music")
            .then(
                (risultato)=>{
                    this.canzoni = risultato.data.response;
                    console.log(this.canzoni);
                    this.caricamento = true;
                }
                )
            .catch()
    },
  
}
</script>

<style lang="scss" scoped>
    .container {
        height: calc(100vh - 80px);
        .canzoni {
            height: 100%;
            align-content: center;
            .canzone {
                margin: 10px 25px;
                
                width: calc( 100%/5 - 50px);
                background-color: #2e3a46;
            }
        }
    }

    .select{
        position: fixed;
        width: 200px;
        top: 25px;
        right: 250px;
    }

    .select2{
        position: fixed;
        width: 200px;
        top: 25px;
        right: 0;
    }

    .caricamento {
        height: calc(100vh - 80px);
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
       
        .caricamento2{
            border: 16px solid #f3f3f3;
            border-radius: 50%;
            border-top: 16px solid #3498db;
            width: 120px;
            height: 120px;
            animation: gira 0.8s linear infinite;
        }

        h4 {
            margin-top: 50px;
            color: white;
        }
        
    }

    
    @keyframes gira {
    from { 
        transform: rotate(0deg);
       }
    to {
        transform: rotate(360deg); 
        
        }
    }

</style>
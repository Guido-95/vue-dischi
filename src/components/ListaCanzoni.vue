<template>
    <div class="container" v-if='caricamento'>
        <div class="canzoni row">
            <div class="select">
                <select @click='ritornaTipo' name="generi" id="generi">
                    <option @click='ritornaTipo' value="Tutti"> Tutti </option>
                    <option @click='ritornaTipo' value="Rock">Rock</option>
                    <option @click='ritornaTipo' value="Pop">Pop</option>
                    <option @click='ritornaTipo' value="Jazz">Jazz</option>
                    <option @click='ritornaTipo' value="Metal">Metal</option>
                </select>
            </div>
            <div class="canzone" v-for="canzone,indicatore in filtraCanzoni" :key="indicatore">

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
import axios from 'axios'
export default {
    name:'ListaCanzoni',
    components:{
        Canzone:Canzone,
    },
    data(){
        return{
            canzoni:[],
            caricamento : false,
            genere: 'Tutti',
        }
    },
     computed: {
        filtraCanzoni: function() {
            console.log("Filtered characters");
           
            if(this.genere == 'Tutti'){
                return this.canzoni;
            }
            const newArray = this.canzoni.filter(
                (element) => {
                   return element.genre == this.genere
                } 
            );
            return newArray;
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
    methods:{
        ritornaTipo(e){
            console.log(e.target.value);
            this.genere = e.target.value;
            console.log(this.filtraCanzoni);
            return e.target.value;
            
        }
    }
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
                height: 350px;
                width: calc( 100%/5 - 50px);
                background-color: #2e3a46;
            }
        }
    }

    .select{
        position: fixed;
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
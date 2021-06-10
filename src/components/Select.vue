<template>
    <div>
        <div class="select">
            <select v-model = "genere" @change ="$emit('cambiamentoSelectGenere', genere)" id="generi">
                <option disabled value = ""> scegli un genere</option>
                <option value = "Tutti"> Tutti</option>
                <option v-for = 'genere,indicatore in arrayFiltrato' :key="indicatore" :value="genere"> {{ genere }} </option>
               
            </select>
            
        </div>
        <!-- <div class="select">
            <select v-model = "autore" 
            @change ="$emit('cambiamentoSelectAutore', autore)" id="generi">
                <option disabled value = ""> scegli un genere</option>
                <option value = "Tutti"> Tutti</option>
                <option v-for = 'genere,indicatore in arrayOggettiCanzoni' :key="indicatore" :value="genere.author"> {{ genere.author }} </option>
               
            </select>
            
        </div>
 -->

        
       
    </div>
</template>

<script>
export default {
    data(){
        return{
            genere:'Tutti',
            autore:'Tutti',
            message:'',
            arrayFiltrato:this.Singolo(),
        }
    },
    props:{
        arrayOggettiCanzoni:Array,
    },

    methods:{
        Singolo(){
            let newArray = []
            this.arrayOggettiCanzoni.forEach(
                (element) => {
                    newArray.push(element.genre);
                }
            );
            newArray = [...new Set(newArray)];
            console.log(newArray);
            return newArray;
        }
    }
  
}
</script>

<style>

</style>
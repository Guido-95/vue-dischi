<template>
     <div class="select">
            <select v-model = "autore" 
            @change ="$emit('cambiamentoSelectAutore', autore)" id="generi">
                <option disabled value = ""> scegli un autore</option>
                <option value = "Tutti"> Autore </option>
                <option v-for = 'genere,indicatore in arrayOggettiCanzoni' :key="indicatore" :value="genere.author"> {{ genere.author }} </option>
               
            </select>
            
        </div>
</template>

<script>
export default {
      data(){
        return {
            autore:'Tutti',
        }
    },
    props:{
        arrayOggettiCanzoni:Array,
    },
}
</script>

<style>

</style>
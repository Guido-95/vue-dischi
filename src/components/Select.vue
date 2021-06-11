<template>
   
    <div class="select">
        <select v-model = "genere" @change ="$emit('cambiamentoSelectGenere', genere)" id="generi">
            <option value = ""> Scegli un Genere </option>
            <option v-for = 'genere,indicatore in arrayFiltrato' :key="indicatore" :value="genere"> {{ genere }} </option>
            
        </select>
        
    </div>

</template>

<script>
export default {
    data(){
        return {
            genere:'',
            arrayFiltrato:this.filtraDoppioni(),
        }
    },
    props:{
        arrayOggettiCanzoni:Array,
    },

    methods: {
        filtraDoppioni() {
            let newArray = []
            this.arrayOggettiCanzoni.forEach(
                (element) => {
                    if (!newArray.includes(element.genre)) {
                      newArray.push(element.genre);
                    }  
                }    
            );
            return newArray;
        }
    }
}
</script>

<style>
    .container-select{
        display: flex;
    }

</style>
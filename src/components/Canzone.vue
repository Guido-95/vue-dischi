<template>
    <div>
        <div class="canzone text-center">
            <img :src="canzone.poster" :alt="canzone.title">
            <h4>{{canzone.title}}</h4>
            <div>{{canzone.author}}</div>
            <div>{{canzone.year}}</div>
        </div>
    </div>
</template>

<script>
export default {
    name:"canzone",
    props:{
        canzone:Object,
    }

}
</script>

<style lang="scss" scoped>
.canzone{
    display: flex;
    flex-direction: column;
    padding:10px;
    img{
        height: 150px;
    }

    h4{
        text-transform: uppercase;
        font-size: 20px;
        margin: 15px;
        color: white;
    }

    div{
        font-weight: 400;
        font-size: 18px;
        color:#807f7e;
    }
    
}
   
</style>
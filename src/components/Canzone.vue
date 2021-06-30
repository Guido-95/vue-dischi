<template>
    <div>
        <div class="canzone text-center">
            <div class="img-disco">
                <img :src="canzone.poster" :alt="canzone.title">
            </div>
            
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
.canzone {
    display: flex;
    flex-direction: column;
    justify-content: center;
    // padding: 20px 8px 20px 8px;
    .img-disco {
        padding-top: 20px;

        img {
        width: 150px;
        }
    }
  

    h4 {
        text-transform: uppercase;
        font-size: 24px;
        margin: 20px 0px 10px 5px;
        color: white;
    }

    div {
        font-weight: 500;
        font-size: 18px;
        color:#807f7e;
    }
    
}
   
</style>
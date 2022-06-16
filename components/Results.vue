<template>
   <p>Reation time Score: {{score}}  ms</p>
   <p class="rank">{{rank}}</p>
</template>

<script>
export default {
    props:['score'],
    data(){
        return{
            rank: null
        }
    },
    mounted(){
       if(this.score < 250){
        this.rank = 'Dimond';
       }else if(this.score < 400){
        this.rank = 'Gold'
       }else{
        this.rank = 'Copper'
       }
    }
}
</script>

<style scoped>
.rank{
    color: yellow;
}
</style>
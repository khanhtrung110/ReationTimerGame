<template>
    <div class="block-click" v-if="showBlock" @click="stopTimer">
        <p>Click Me</p>
    </div>    
</template>
<script>
    export default{
        props:['delay'],
        data(){
            return {
                showBlock: false,
                timer: null,
                retionTime: 0
            }
        },
        methods:{
            startTimer(){   
                this.timer = setInterval(()=>{
                    this.retionTime += 10 
                }, 10)
            },
            stopTimer(){
                clearInterval(this.timer)
                console.log(this.retionTime)
                this.$emit('end',this.retionTime)
            }
        },
        mounted(){
            setTimeout(()=>{
                this.showBlock = true
                console.log(this.delay)
                this.startTimer()
            },this.delay)
        }
    }
</script>


<style scoped>
.block-click{
    width: 404px;
    margin: 20px auto;
    background: green;
    color: white;
    padding: 100px 0;
}
p{
    text-align: center;
}
</style>
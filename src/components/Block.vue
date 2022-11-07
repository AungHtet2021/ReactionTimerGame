<template>
    <div class="block" v-if="showblock" @click="stopTimer">Click here{{delay}}</div>
</template>

<script >
export default {
    props:['delay'],
    data(){
        return{
            showblock:false,
            score:0,
            timer:null
        }
    },
    mounted(){
        setTimeout(() => {
            this.showblock=true;
            this.startTimer()
        }, this.delay);
    },
    methods:{
        startTimer(){
           this.timer= setInterval(()=>{
           this.score+=50;
            },50)
        },
        stopTimer(){
            clearInterval(this.timer)
            this.$emit("endGame",this.score)
        }
    },
  }
</script>

<style  scoped>
    .block{
        background-color: crimson;
        width: 500px;
        height: 400px;
        margin:30px auto;
        padding-top:30px;
        font-size: 20px;

    }
</style>
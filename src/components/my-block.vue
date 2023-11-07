<template>
  <div class="block" v-if="showBlock" @click ="stopTimer">
    Click Me
  </div>
</template>

<script>
export default {
   props: ['delay'],
   data(){
    return{
        showBlock:false,
        timer: null,
        reactiontime: 0
    }
   },
   mounted(){
    console.log("Component mounted");
    setTimeout(() => {
        this.showBlock = true;
        this.startTimer();
    }, this.delay);
   },
   updated(){
    console.log("Component updated");
   },
   methods:{
    startTimer(){
        this.timer = setInterval(()=>{
           this.reactiontime += 10;
        },10) 
    },
    stopTimer(){
       clearInterval(this.timer);
       this.$emit('end',this.reactiontime);
    }
   }
}
</script>

<style>
.block{
    width: 400px;
    border-radius: 20px;
    background: #0faf87;
    color: white;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
}
</style>
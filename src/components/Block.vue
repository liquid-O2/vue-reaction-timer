<template>
  <div class="block" v-show="showBlock" @click="stopTimer">
      Click Here
  </div>
</template>

<script>

export default {
 props:[
     'delay'
 ],
 data(){
     return{
     showBlock:false,
     timer:null,
     rcnTimer:0,
     }
 },
 mounted(){
     console.log('component mounted')
     setTimeout(() => {
         this.showBlock = true
         this.startTimer()
     } ,this.delay)
 },
 methods:{
     startTimer(){
    setInterval(() => {
        this.rcnTimer += 10
    },10);
     },
     stopTimer(){
         
         clearInterval(this.timer)
         this.$emit('end', this.rcnTimer)
        console.log(this.rcnTimer)
     }
 }
}
</script>

<style>
.block{
    margin:2rem auto;
    width:50%;
    text-align: center;
    padding: 5rem;
    cursor: pointer;
    background-color:#adb3bc;
    border-radius: 3rem;
    color:#f4f4f4
}
</style>
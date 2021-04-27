<template  >
  <h1>Test Your Reaction Time</h1>
  <button @click="toggleGame" :disabled="isPlaying" > Start Game</button>
  <Block v-if="isPlaying" :delay="delay" @end="stopG" />
   <Results v-if="showScore" :Score="score"/>
</template>

<script>
import Block from './components/Block'
import Results from './components/Results'
export default {
  name: 'App',
  data(){
    return{
      isPlaying:false,
      delay:null,
      score:null,
      showScore:false
    }
  },
  components: {
   Block, Results
  },
  methods:{
    toggleGame(){
      this.isPlaying= true
      this.delay= 200 + Math.random()*5000
      this.showScore=false
    },
    stopG(rcnTimer){
      console.log('this is working')
       this.score = rcnTimer
       this.isPlaying = false
       this.showScore= true
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}
button{
  padding: 1rem;
  border-radius: 1rem;
  border-color:transparent;
  background: #53565a;
  color:#f4f4f4
}
.Disabled{
  background: #c0c8d1;
}
</style>

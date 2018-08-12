<template>
  <div id="app">
    <input v-model='input' style="text-align:right"/>
    <div>
      <button class="symbol" @click="sign('div')">÷</button>
      <button class="symbol" @click="sign('mul')">x</button>
      <button class="symbol" @click="sign('sub')">-</button>
      <button class="symbol" @click="sign('add')">+</button>
    </div>
    <div>
      <button @click="append(7)">7</button>
      <button @click="append(8)">8</button>
      <button @click="append(9)">9</button>
    </div>
    <div>
      <button @click="append(4)">4</button>
      <button @click="append(5)">5</button>
      <button @click="append(6)">6</button>
    </div>
    <div>
      <button @click="append(1)">1</button>
      <button @click="append(2)">2</button>
      <button @click="append(3)">3</button>
    </div>
    <div>
      <button @click="append('.')">.</button>
      <button @click="append(0)">0</button>
      <button @click="equal">=</button>
    </div>
  </div>
</template>

<script>

export default {
  name: "App",
  data(){
    return{
      input:'',
      firstpart:'',
      symbol:'',
      secondpart:'',
    }
  },
  methods:{
    append(num){
      this.input+=num;
    },
    sign(s){
      this.symbol=s;
      this.firstpart=parseFloat(this.input);
      this.input='';
    },
    equal(){
      this.secondpart=parseFloat(this.input);
      if(this.symbol==='div'){
        this.input=this.firstpart/this.secondpart;
      } else if(this.symbol==='mul'){
        this.input=this.firstpart*this.secondpart;
      } else if(this.symbol==='sub'){
        this.input=this.firstpart-this.secondpart;
      } else {
        this.input=this.firstpart+this.secondpart;
      }
    }
  }
};
</script>

<style>
button{
  font-size:40px;
  width:12%;
}
.symbol{
  width:9%;
}
input{
  width:36%;
  height:30px;
}
</style>

<template>
  <div>
    <input v-model.number="num" v-on:input="initCounters()"/>
    <div v-if="parseInt(num)">
      <Counter 
        v-for="n in parseInt(num)" 
        v-bind:key="n" 
        v-bind:index="n" 
        v-bind:count="counter[n-1]"
        v-on:update="updateCountList"/>
      <span >sum:{{sum}}</span>
    </div>
  </div>
</template>

<script>
import Counter from "./component/Counter.vue";

export default {
  name: "app",
  data:function() {
    return {
      num: 0,
      counter:[],
      sum:0
    };
  },
  components: {
    Counter
  },
  methods:{
    getSum(){
        this.sum = 0;
        for (var i = 0; i < this.counter.length; i++) {
          this.sum += this.counter[i];
        }
    },
    updateCountList:function(data){
        console.log(data);
        this.counter[data.index - 1] = data.value;
        this.getSum();
    },
    initCounters(){
      let length = parseInt(this.num);
      if(length == 0){
          this.counter = [];
      }else{
        for(let i = 0;i < this.num;i++){
            this.counter.push(i+1);
        }
      }
        
        this.getSum();
    }
  }
};
</script>

<style>
</style>

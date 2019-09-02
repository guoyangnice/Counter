<template>
  <div>
    <span>{{index}}：</span>
    <button @click="inc">+</button>
    <span>{{count}}</span>
    <button @click="dec">-</button>
  </div>
  
</template>

<script>
export default {
  name: "Counter",
  props: {
    index: Number,
    count:Number
  },
  methods: {
    //增加
    inc() {
      this.$emit('update',{
					index : this.index,
					value: this.count+1
				});
    },
    //减少
    dec() {
      this.$emit('update',{
                index : this.index,
                value: this.count-1
          });
    },
  }
};
</script>

<style>
</style>

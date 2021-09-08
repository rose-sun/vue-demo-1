<template>
 <div>
   {{n}}
  <div class="cell" v-on:click="clickSelf">
    <template v-if="a">{{ text }}</template>
    <template v-else></template>
  </div>
  </div>
</template>
<script>
export default {
  props:["n"],
  data() {
    //ES6语法
    return { a: false, text:"" };
  },
  methods: {
    clickSelf() {
      if(this.text !== ""){
        return;
      }
      this.a = true;
      this.text = this.n % 2===0 ? "x":"o";
      this.$emit(this.text)  //告诉内容
    },
  },
};
</script>

<style>
.cell {
  border: 1px solid black;
  height: 100px;
  width: 100px;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 50px;
}
</style>

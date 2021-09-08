<template>
  <div>
    <div>n的值是{{ n }}</div>
    <div class="row">
      <Cell @click="onCellClick(0, $event)" :n="n" />
      <Cell @click="onCellClick(1, $event)" :n="n" />
      <Cell @click="onCellClick(2, $event)" :n="n" />
    </div>
    <div class="row">
      <Cell @click="onCellClick(3, $event)" :n="n" />
      <Cell @click="onCellClick(4, $event)" :n="n" />
      <Cell @click="onCellClick(5, $event)" :n="n" />
    </div>
    <div class="row">
      <Cell @click="onCellClick(6, $event)" :n="n" />
      <Cell @click="onCellClick(7, $event)" :n="n" />
      <Cell @click="onCellClick(8, $event)" :n="n" />
    </div>
    <div>{{map}}</div>
    <div>{{result}}</div>
  </div>
</template>
<script>
import Cell from "./Cell";
export default {
  components: { Cell },
  data() {
    return {
      n: 0,
      map: [
        [null, null, null],
        [null, null, null],
        [null, null, null],
      ],
      result: false
    };
  },
  methods: {
    onCellClick(i, text) {
      console.log(`${i}号被点击，内容是:${text}`);
      this.map[Math.floor(i/3)][i%3] = text
      this.n += 1;
      this.tell();
    },

    tell(){
      const map = this.map
      for(let i=0; i<3;i++){
      if(map[i][0] !== null && map[i][0] == map[i][1] && map[i][1] == map[i][2]){   //一行相同且不为空，赢了
        this.result = true;
      }
      }
    }
  },
};
</script>

<style>
.row {
  display: flex;
}
</style>

<template>
  <div >
    <div class="row">
      <Cell @click="onClickCell(0,$event)" :n="n"/>
      <Cell @click="onClickCell(1,$event)" :n="n"/>
      <Cell @click="onClickCell(2,$event)" :n="n"/>
    </div>
    <div class="row">
      <Cell @click="onClickCell(3,$event)" :n="n"/>
      <Cell @click="onClickCell(4,$event)" :n="n"/>
      <Cell @click="onClickCell(5,$event)" :n="n"/>
    </div>
    <div class="row">
      <Cell @click="onClickCell(6,$event)" :n="n"/>
      <Cell @click="onClickCell(7,$event)" :n="n"/>
      <Cell @click="onClickCell(8,$event)" :n="n"/>
    </div>
<div>{{map}}</div>
<div>{{result}}</div>
  </div>
</template>

<script>
import Cell from "./Cell.vue";
export default {
  components: { Cell },
  data(){
    return {
      n:0,
      map:[
        [null,null,null],
        [null,null,null],
        [null,null,null],
      ],
      result:false
    }
  },
  methods:{
    onClickCell(i,text){
      console.log(`${i}号被点击，内容是：${text}`)
      this.map[Math.floor(i/3)][i%3] = text
      this.n+=1
      this.tell()
    },
    tell(){
      const map = this.map
      for(let i=0;i<2;i++){
        if(map[i][0] !== null && map[i][0] === map[i][1] && map[i][1] === map[i][2]){
          this.result = map[i][0]
        }
      }
      for(let j=0;j<2;j++){
        if(map[0][j] !== null && map[0][j] === map[1][j] && map[1][j] === map[2][j]){
          this.result = map[0][j]
        }
      }
      if(map[0][0] !== null && map[0][0] === map[1][1] && map[1][1] === map[2][2]){
          this.result = map[0][0]
      }
      if(map[0][2] !== null && map[0][2] === map[1][1] && map[1][1] === map[2][0]){
          this.result = map[0][2]
      }
    }
  }
};
</script>

<style>

.row{
  display:flex;
}
</style>

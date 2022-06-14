<template>
  <div class="hello">
    
    <div class="row" v-for="row in _board" :key="row[0].row">
      <div class="boardSquare" v-for="square in row" :key="square.id" :style="{'background-color': _board[square.row][square.col].value}" @click="play">
        {{square.id}}
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import Tetris from './tetris/Tetris.vue';

@Component
export default class HelloWorld extends Vue {
  private board: { value: String, row: number, col: number, id: number }[][];
  private t: Tetris;

  constructor() {
    super();
        this.board = new Array();

        let i: number = 0;
        while(i < 20) {
          this.board[i] = new Array();
          let j: number = 0;
          while(j < 10) {
            let id = i*10 + j;
            this.board[i][j] = { value: "green", id: id, row: i, col: j };
            j++;
          }
          i++;
        }

        this.t = new Tetris();
        console.log(this.t.testFunction());
  }

  
  public get _board() : Array<{value: String, id: number, row: number, col: number}[]> {
    return this.board;
  }


  


  toggleSquare(row: number, col: number) {

    this.board[row][col].value = "black";

    return true;
  }

  sleep(ms:number) {
    return new Promise((resolve) => {
      setTimeout(resolve, ms);
    })
  }


  async play() {
    let i: number = 0;
    while(i < 20) {
      this.toggleSquare(i, 4);
      await this.sleep(1000);
      i++;
    }
  }



}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.boardSquare {
  width: 4.5vw;
  height: 4.5vw;
  border: 0.5vw solid;
  background-color: #fff;
  flex-flow: column;
}

.boardSquare:hover {
  background-color: grey;
}

.row {
  display: flex;
  background-color: gray;
  width: 100%;
}
</style>

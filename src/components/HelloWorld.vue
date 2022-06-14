<template>
  <div class="hello">
    
    <div class="row" v-for="row in 20" :key="row">
      <div class="boardSquare" v-for="square in 10" :key="square">
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';

@Component
export default class HelloWorld extends Vue {
  @Prop() private msg!: string;
  private board: boolean[];

  constructor() {
    super();
        this.board = new Array<boolean>();
        this.board[0] = true;
        this.board[1] = true;
        this.board[2] = true;
        this.board[3] = true;
        this.board[4] = true;
  }

  beforeCreate() {
    
  }


}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.boardSquare {
  width: 48px;
  height: 48px;
  border: 1px solid;
  background-color: #fff;
  flex-flow: column;
}

.boardSquare:hover {
  background-color: grey;
}

.row {
  display: flex;
  background-color: gray;
  width: 500px;
}
</style>

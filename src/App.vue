<template>
  <div class="game" :class="{no_events: counter === 6}">
    <div class="board">
      <div class="row" v-for="(row, i) in board" :key="row">
        <div class="cell" :class="[cell]" @click="setColor(i, j)" v-for="(cell, j) in row" :key="cell">
          </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'App',
    data(){
      return{
        board: [
          ["", "", ""],
          ["", "", ""],
        ],
        colors: [
          ["red", "blue", "green"],
          ["blue", "red", "green"],
        ],
        counter: 0,

      }

    },
    methods:{
      setColor(i, j){
        this.board[i][j] = this.colors[i][j];

        for (let i = 0; i < 2; i++) {
          for (let j = 0; j < 3; j++) {
            if (this.board[i][j] !== "") {
              this.counter++;
            }
          }

        }
        if (this.counter === 6) {
          console.log("Koniec Gry");
        }
        console.log(this.counter);
      }
    }
  }
</script>

<style>
  .red{
    background-color: red;
  }
  .green{
    background-color: green;
  }
  .blue{
    background-color: blue;
  }
  .game{
    display: flex;
    justify-content: center;
  }
  .cell{
    width: 200px;
    height: 200px;
    border: 1px solid black;
    cursor: pointer;
  }
  .board{
    width: 600px;
    display: flex;
    flex-direction: column;
  }
  .row{
    width: 600px;
    display: flex;
  }
  .no_events{
    pointer-events: none;
  }
</style>



<template>
  <div>
    <board />


  </div>
</template>

<script >
import board from './components/Board.vue';
export default { components: { board } }
/* import {ref,computed} from 'vue'
const player = ref('x');
const board = ref(
     [ '','',''],
  [ '','',''],
    [ '','','']
)


const calculateWinner=(squares)=> {
  const lines = [
    [0, 1, 2],
    [3, 4, 5],
    [6, 7, 8],
    [0, 3, 6],
    [1, 4, 7],
    [2, 5, 8],
    [0, 4, 8],
    [2, 4, 6],
  ];
  for (let i = 0; i < lines.length; i++) {
    const [a, b, c] = lines[i]
    if (squares[a] && squares[a] === squares[b] && squares[a] === squares[c]) {
      return squares[a]
    }
  }
  return null;
};
const winner = computed(()=> calculateWinner(board.value.flat()))
const makemove=(x,y) => {

    if (winner.value) return

    if (board.value[x][y]!='')return
    board.value[x][y]=player.value
    player.value = player.value ==='X' ? 'O' : 'X'
  

}
const resetGame=()=>{
  board.value = [
  ['','',''],
  ['','',''],
  ['','','']
]
player.value ='X'

}
*/
</script>

<style>
.app {
  background-color: aqua;
}
</style>

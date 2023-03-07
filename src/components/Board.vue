<template>
    <div class="container">
        <h2 v-if="winner"> Winner : {{ winner }}</h2>
        <h2 v-else> {{ msg }}</h2>
        <button @click="reset">Reset</button>
        <div v-for="x in 3" :key="x" class="row">
            <button v-for="y in 3" :key="y" @click="move(x - 1, y - 1)" class="square">
                <h1>{{ squares[x - 1][y - 1] }}</h1>
            </button>

        </div>
    </div>
</template>


<script >
import { ref, computed } from 'vue'
const calculateWinner = squares => {
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
}


export default {
    setup() {
        const turn = ref(0)
        const msg = ref('player move : ')
        const player = ref('X')
        const squares = ref([
            ['', '', ''],
            ['', '', ''],
            ['', '', '']
        ]
        )
        const winner = computed(() => calculateWinner(squares.value.flat()))
        const move = (x, y) => {
            if ((squares.value[x][y] === 'O') || (squares.value[x][y] === 'X')) return null;
            if (winner.value) return
            squares.value[x][y] = player.value
            player.value = player.value === 'O' ? 'X' : 'O'
            msg.value = 'player move : ' + player.value
            turn.value = turn.value + 1
            if (turn.value == 9) {
                msg.value = 'Game Draw'
            }


        }
        const reset = () => {
            player.value = 'X'
            squares.value = [
                ['', '', ''],
                ['', '', ''],
                ['', '', '']]
            msg.value = 'player move : '
            turn.value = 0
        }


        return { winner, player, squares, move, reset, msg, turn }
    }
}


</script>



<style>
h2 {
    color: #DFF6FF;
}

.row {
    padding: 1rem;
    justify-content: center;
    margin: 1rem;
    color: #B2B2B2;

}

.square {
    padding: 1rem;
    width: 5rem;
    height: 5rem;
    margin: 0.5rem;
    color: #47B5FF;

}

.container {
    margin: 10% auto;
    text-align: center;
    width: 30%;
    border: 3px solid green;
    padding: 10px;
    display: flexbox;
    background-color: #06283D;
}
</style>
<script setup>
import { ref, computed, watch, onMounted } from 'vue'

const player = ref('X')
const num = ref(3)
const showhistory = ref(false)
const squares = ref([
    ['', '', ''],
    ['', '', ''],
    ['', '', '']
])
const historywinplayer = ref('')
const historywinindex = ref('')
const pattern = ref([])
const ishistory = ref(false)
const calsquares = computed(() => {
    player.value = 'X'
    if (ishistory.value == false) {
        if (num.value == 3) {
            squares.value = [
                ['', '', ''],
                ['', '', ''],
                ['', '', '']
            ]
        } else if (num.value == 4) {
            squares.value = [
                ['', '', '', ''],
                ['', '', '', ''],
                ['', '', '', ''],
                ['', '', '', '']
            ]
        } else if (num.value == 5) {
            squares.value = [
                ['', '', '', '', ''],
                ['', '', '', '', ''],
                ['', '', '', '', ''],
                ['', '', '', '', ''],
                ['', '', '', '', '']
            ]
        }
    }

})
const calculateWinnerX3 = squares => {
    const lines = [
        [0, 1, 2],
        [3, 4, 5],
        [6, 7, 8],
        [0, 3, 6],
        [1, 4, 7],
        [2, 5, 8],
        [0, 4, 8],
        [2, 4, 6]
    ]
    if (!ishistory.value) {
        for (let i = 0; i < lines.length; i++) {
            const [a, b, c] = lines[i];
            if (squares[a] === squares[a] && squares[a] === squares[b] && squares[a] === squares[c]) {
                pattern.value = squares
                return squares[a]
            }
        }
        if (squares.every(square => square === 'X' || square === 'O')) {
            pattern.value = squares
            return 'Draw';
        }
    }

}
const calculateWinnerX4 = squares => {
    const lines = [
        [0, 1, 2, 3],
        [4, 5, 6, 7],
        [8, 9, 10, 11],
        [12, 13, 14, 15],
        [0, 4, 8, 12],
        [1, 5, 9, 13],
        [2, 6, 10, 14],
        [3, 7, 11, 15],
        [0, 5, 10, 15],
        [3, 6, 9, 12]
    ]
    if (!ishistory.value) {
        for (let i = 0; i < lines.length; i++) {
            const [a, b, c, d] = lines[i];
            if (squares[a] === squares[a] && squares[a] === squares[b] && squares[a] === squares[c] && squares[a] === squares[d]) {
                pattern.value = squares
                return squares[a]
            }
        }
        if (squares.every(square => square === 'X' || square === 'O')) {
            pattern.value = squares
            return 'Draw';
        }
    }
}
const calculateWinnerX5 = squares => {
    const lines = [
        [0, 1, 2, 3, 4],
        [5, 6, 7, 8, 9],
        [10, 11, 12, 13, 14],
        [15, 16, 17, 18, 19],
        [20, 21, 22, 23, 24],
        [0, 5, 10, 15, 20],
        [1, 6, 11, 16, 21],
        [2, 7, 12, 17, 22],
        [3, 8, 13, 18, 23],
        [4, 9, 14, 19, 24],
        [0, 6, 12, 18, 24],
        [4, 8, 12, 16, 20]
    ]
    if (!ishistory.value) {
        for (let i = 0; i < lines.length; i++) {
            const [a, b, c, d, e] = lines[i];
            if (squares[a] === squares[a] && squares[a] === squares[b] && squares[a] === squares[c] && squares[a] === squares[d] && squares[a] === squares[e]) {
                pattern.value = squares
                return squares[a]
            }
        }
        if (squares.every(square => square === 'X' || square === 'O')) {
            pattern.value = squares
            return 'Draw';
        }
    }
}
const move = (x, y) => {
    if (winner.value) return
    squares.value[x][y] = player.value
    player.value = player.value === 'O' ? 'X' : 'O'

}
const reset = () => {
    ishistory.value = false
    player.value = 'X'
    if (num.value == 3) {
        squares.value = [
            ['', '', ''],
            ['', '', ''],
            ['', '', '']
        ]
    } else if (num.value == 4) {
        squares.value = [
            ['', '', '', ''],
            ['', '', '', ''],
            ['', '', '', ''],
            ['', '', '', '']
        ]
    } else if (num.value == 5) {
        squares.value = [
            ['', '', '', '', ''],
            ['', '', '', '', ''],
            ['', '', '', '', ''],
            ['', '', '', '', ''],
            ['', '', '', '', '']
        ]
    }
}

const showpattern = async (index) => {
    ishistory.value = true
    historywinplayer.value = history.value[index].win
    historywinindex.value = index
    num.value = history.value[index].size
    if (num.value == 3) {
        squares.value = [
            [history.value[index].pattern[0], history.value[index].pattern[1], history.value[index].pattern[2]],
            [history.value[index].pattern[3], history.value[index].pattern[4], history.value[index].pattern[5]],
            [history.value[index].pattern[6], history.value[index].pattern[7], history.value[index].pattern[8]]
        ]
    }
    if (num.value == 4) {
        squares.value = [
            [history.value[index].pattern[0], history.value[index].pattern[1], history.value[index].pattern[2], history.value[index].pattern[3]],
            [history.value[index].pattern[4], history.value[index].pattern[5], history.value[index].pattern[6], history.value[index].pattern[7]],
            [history.value[index].pattern[8], history.value[index].pattern[9], history.value[index].pattern[10], history.value[index].pattern[11]],
            [history.value[index].pattern[12], history.value[index].pattern[13], history.value[index].pattern[14], history.value[index].pattern[15]]
        ]
    }
    if (num.value == 5) {
        squares.value = [
            [history.value[index].pattern[0], history.value[index].pattern[1], history.value[index].pattern[2], history.value[index].pattern[3], history.value[index].pattern[4]],
            [history.value[index].pattern[5], history.value[index].pattern[6], history.value[index].pattern[7], history.value[index].pattern[8], history.value[index].pattern[9]],
            [history.value[index].pattern[10], history.value[index].pattern[11], history.value[index].pattern[12], history.value[index].pattern[13], history.value[index].pattern[14]],
            [history.value[index].pattern[15], history.value[index].pattern[16], history.value[index].pattern[17], history.value[index].pattern[18], history.value[index].pattern[19]],
            [history.value[index].pattern[20], history.value[index].pattern[21], history.value[index].pattern[22], history.value[index].pattern[23], history.value[index].pattern[24]]
        ]
    }

}
const history = ref([])
const winner = computed(() => num.value == 3 ? calculateWinnerX3(squares.value.flat()) : num.value == 4 ? calculateWinnerX4(squares.value.flat()) : calculateWinnerX5(squares.value.flat()))
watch(winner, (current, previous) => {
    if (current == 'Draw') {
        history.value.push({ win: 'Draw', pattern: pattern.value, size: num.value })
        localStorage.setItem('perm-tictactoe-history', JSON.stringify(history.value))
    } else if (current && !previous) {
        history.value.push({ win: current, pattern: pattern.value, size: num.value })
        localStorage.setItem('perm-tictactoe-history', JSON.stringify(history.value))
    }
})
onMounted(() => {
    const his = JSON.parse(localStorage.getItem('perm-tictactoe-history'))
    if (his !== undefined && his !== null) {
        history.value = his
    } else {
        history.value = []
    }
})
</script>
<template>
    <div class="space-y-8">
        <div class="hidden">{{ calsquares }}</div>
        <div class="text-center space-y-2">
            <div v-if="winner && winner != 'Draw'">Winner: {{ winner }}</div>
            <div v-if="winner && winner == 'Draw'">Draw</div>
            <div v-if="!winner && !ishistory">Player Turn: {{ player }}</div>
            <div v-if="ishistory">Game {{ historywinindex + 1 }}: {{ historywinplayer }} <span v-if="historywinplayer !== 'Draw'">won</span></div>
            <div v-if="!ishistory">

                <select class="border border-black rounded-md" v-model="num" @change="calsquares">
                    <option :value="3">3</option>
                    <option :value="4">4</option>
                    <option :value="5">5</option>
                </select>
            </div>
            <div>
                <button class="p-2 bg-red-200 hover:bg-red-300 active:bg-red-400 rounded-md" @click="reset">Reset</button>
            </div>
        </div>
        <div>
            <div class="flex justify-center " v-for="(_, x) in num" :key="x">
                <div class="border border-black m-1 w-12 h-12 flex justify-center items-center" v-for="(_, y) in num"
                    :key="y"
                    @click="squares[x][y] == 'X' || squares[x][y] == 'O' ? '' : ishistory == true ? '' : move(x, y)">
                    <div>{{ squares[x][y] }}</div>
                </div>
            </div>
        </div>
        <div class="text-center space-y-4">

            <button class="p-2 rounded-md bg-green-200 hover:bg-green-300 active:bg-green-400"
                @click="showhistory = !showhistory">
                Show History
            </button>
            
            <div class="bg-green-100 hover:bg-green-200 active:bg-green-300 cursor-pointer w-fit mx-auto rounded-md " v-if="showhistory" v-for="(won, index) in history" :key="index" @click="showpattern(index)">
                Game {{ index + 1 }}: {{ won.win }} <span v-if="won.win != 'Draw'">won</span>
            </div>
            <div v-if="history.length == 0" v-show="showhistory">
                    No History
            </div>
        </div>
    </div>
</template>
 
<style scoped>
</style>

<script setup>
import { ref } from 'vue'

const selected = ref({
    dice1: false,
    dice2: false,
    dice3: false,
    dice4: false,
    dice5: false,
})
const dice = ref(["&#x2680;", "&#x2681;", "&#x2682;", "&#x2683;", "&#x2684;"])

const diceModel = defineModel()

function roll() {
    for (let i=0; i<5; i++)
        if (!selected.value['dice' + (i+1)]) {
            const diceValue = Math.ceil(Math.random() * 6)
            diceModel.value[i] = diceValue
            dice.value[i] = "&#x268" + (diceValue - 1) + ";"
        }
}

function diceClick(e) {
    const buttonId = e.srcElement.parentElement.id
    selected.value[buttonId] = !selected.value[buttonId]
}
</script>

<template>
    <div class="fiveDice">
        <button @click="diceClick" id="dice1" :class="[{ selected: selected.dice1 }, dice]"><div v-html="dice[0]"></div></button>
        <button @click="diceClick" id="dice2" :class="[{ selected: selected.dice2 }, dice]"><div v-html="dice[1]"></div></button>
        <button @click="diceClick" id="dice3" :class="[{ selected: selected.dice3 }, dice]"><div v-html="dice[2]"></div></button>
        <button @click="diceClick" id="dice4" :class="[{ selected: selected.dice4 }, dice]"><div v-html="dice[3]"></div></button>
        <button @click="diceClick" id="dice5" :class="[{ selected: selected.dice5 }, dice]"><div v-html="dice[4]"></div></button>
    </div>
    <div class="button">
        <button @click="roll" id="btn" class="btn wHover">Gooien</button>
    </div>
</template>

<style>
.fiveDice .dice {
    width: 100px;
    height: 100px;
    line-height: 100px;
}
.selected {
    filter: invert(.5);
}
</style>

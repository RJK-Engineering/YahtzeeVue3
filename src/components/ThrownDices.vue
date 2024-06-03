<script setup>
import { ref } from 'vue'
const throws = ref([1, 1, 1, 1, 1])
const dice = ref(["&#x2680;", "&#x2681;", "&#x2682;", "&#x2683;", "&#x2684;"])

function gooi() {
    throws.value = throws.value.map(() => Math.ceil(Math.random() * 6));
    dice.value = throws.value.map((e) => "&#x268" + (e-1) + ";");
    console.debug(throws.value);
}

function keep(e) {
    const button = e.srcElement.parentElement;
    button.style.filter = "invert(.5)";
    console.log(button.id);
}

</script>

<template>
    <div class="fiveDice">
        <button @click="keep" id="dice1" class="dice textHover"><div v-html="dice[0]"></div></button>
        <button @click="keep" id="dice2" class="dice textHover"><div v-html="dice[1]"></div></button>
        <button @click="keep" id="dice3" class="dice textHover"><div v-html="dice[2]"></div></button>
        <button @click="keep" id="dice4" class="dice textHover"><div v-html="dice[3]"></div></button>
        <button @click="keep" id="dice5" class="dice textHover"><div v-html="dice[4]"></div></button>
    </div>
    <div class="button">
        <button @click="gooi" id="btn" class="btn wHover">Gooien</button>
    </div>
</template>

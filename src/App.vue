<script setup>
import ThrownDices from './components/ThrownDices.vue'
import ScoreTable from './components/ScoreTable.vue'

import { ref } from 'vue'
const diceModel = ref([1, 2, 3, 4, 5])
const frequency = ref([0, 0, 0, 0, 0, 0])

function addThrow() {
    frequency.value = [0, 0, 0, 0, 0, 0]
    for (var i=0; i<diceModel.value.length; i++)
        frequency.value[diceModel.value[i] - 1]++
}
</script>

<template>
  <main>
    <div id="container">
        <header>
            <h1>Yahtzee</h1>
        </header>

        <ThrownDices v-model="diceModel" />

        <div class="button">
            <button @click="addThrow" id="btnFill" class="btn wHover">Vul score in</button>
        </div>

        <div class="round">
            <p id="rounds"></p>
        </div>

        <div class="howTo">
            <p>Klik <span class="borderBtn">Gooien</span> om de dobbelstenen te gooien, klik op een dobbelsteen om de waarde vast te houden.</p>
            <p>Na drie worpen klik je op <span class="borderBtn">Vul score in</span> om de score in te vullen.</p>
            <p>Kies welke score je wil vastleggen op het scoreblok.</p>
        </div>

        <ScoreTable :frequency="frequency" />
    </div>
  </main>
</template>

<style>
html, body, div, span, applet, object, iframe,
h1, h2, h3, h4, h5, h6, p, blockquote, pre,
a, abbr, acronym, address, big, cite, code,
del, dfn, em, img, ins, kbd, q, s, samp,
small, strike, strong, sub, sup, tt, var,
b, u, i, center,
dl, dt, dd, ol, ul, li,
fieldset, form, label, legend,
table, caption, tbody, tfoot, thead, tr, th, td,
article, aside, canvas, details, embed,
figure, figcaption, footer, header, hgroup,
menu, nav, output, ruby, section, summary,
time, mark, audio, video {
  margin: 0;
  padding: 0;
  border: 0;
  font-size: 100%;
  font: inherit;
  vertical-align: baseline;
}
/* HTML5 display-role reset for older browsers */
article, aside, details, figcaption, figure,
footer, header, hgroup, menu, nav, section {
  display: block;
}
body {
  line-height: 1;
  margin: 0;
}
ol, ul {
  list-style: none;
}
blockquote, q {
  quotes: none;
}
blockquote:before, blockquote:after,
q:before, q:after {
  content: '';
  content: none;
}
table {
  border-collapse: collapse;
  border-spacing: 0;
}

#container {
  width: 780px;
  margin: auto;
}

header {
  text-align: center;
  margin-top: 50px;
}

header h1 {
  font-size: 60px;
  font-family: Anton, sans-serif;
  font-weight: bold;
  letter-spacing: 0.1em;
  color: black;
}

.fiveDice {
  display: flex;
  flex-wrap: nowrap;
  margin: auto;
  justify-content: center;
  align-items: center;
}

button {
  text-decoration: none;
  color: black;
  background-color: transparent;
  border: none;
  cursor: pointer;
}

.fiveDice button {
  font-size: 100px;
  width: 75px;
  height: 120px;
}

.onHover:hover {
  box-shadow: 0px 0px 10px 0px rgba(0,0,0,0.75);
  transition-duration: 0.5s;
  transition-timing-function: ease-in;
}

.touchHover:hover {
  transition-duration: 0.5s;
  transition-timing-function: ease-in;
}

.onTextHover:hover {
  text-shadow: 0px 0px 10px rgba(0, 155, 0, 0.5);
  transition-duration: 0.5s;
}

.touchTextHover:hover {
  transition-duration: 0.5s;
}

.button {
  text-align: center;
  margin: 20px 0 30px 0;
}

.button .btn {
  border: 5px solid black;
  font-size: 18px;
  font-weight: bold;
  width: 140px;
  padding: 10px 0;
}

.round {
  font-family: Helvetica, sans-serif;
  text-align: center;
  font-size: 14px;
  text-transform: capitalize;
  padding-bottom: 10px;
}

#btn {
  margin-right: 10px;
}

#btnFill {
  margin-left: 10px;
}

.howTo {
  font-family: Helvetica, sans-serif;
  font-size: 10px;
  text-align: center;
  margin: 0 0 30px 0;
  color: rgba(0, 0, 0, 0.7);
}

p:first-child,
p:nth-child(2) {
  margin: 0 0 15px 0;
}

span.borderBtn {
  border: 1px solid rgba(0, 0, 0, 0.7);
  padding: 3px;
}

table {
  margin: 0px auto 50px auto;
}

th,
td {
  font-family: Helvetica, sans-serif;
  width: 75px;
  height: 50px;
  text-align: center;
  vertical-align: middle;
  border: 2px solid rgba(0, 0, 0, 0.9);
}

th, td.h2 {
  font-weight: bold;
}

th.title {
  background-color: rgba(0, 0, 0, 0.9);
  color: rgba(255, 255, 255, 0.9);
  font-family: 'Heebo', sans-serif;
  text-transform: uppercase;
  font-size: 50px;
  padding: 10px 0 10px 0;
}

img.posImg {
  position: absolute;
  top: 35px;
  left: 450px;
  transform: rotate(-5deg);
  height: 150px;
}

th.h1 {
  font-size: 18px;
  font-weight: bold;
  text-transform: uppercase;
}

th.h2,
td.h2 {
  font-size: 14px;
}

th.h2,
th.h3, {
  height: 60px;
}

th:nth-child(1),
td:nth-child(1){
  width: 110px;
  text-align: left;
  padding-left: 10px;
}

td {
  font-size: 12px;
  color: rgba(0, 0, 0, 0.9);
}

td.noBorderRight {
  border-top: 2px solid rgba(0, 0, 0, 0.9);
  border-bottom: 2px solid rgba(0, 0, 0, 0.9);
  border-left: 2px solid rgba(0, 0, 0, 0.9);
  border-right: 0px solid rgba(0, 0, 0, 0.9);
}

td.noBorderLeft {
  border-top: 2px solid rgba(0, 0, 0, 0.9);
  border-bottom: 2px solid rgba(0, 0, 0, 0.9);
  border-left: 0px solid rgba(0, 0, 0, 0.9);
  border-right: 2px solid rgba(0, 0, 0, 0.9);
}

th.noBorder,
td.noBorder {
  border: 0px solid rgba(0, 0, 0, 0.9);
}

td.check {
  background-color: rgba(0, 100, 0, 0.5);
  cursor: pointer;
  transition-duration: 0.5s;
  transition-timing-function: ease-in;
}

td.uppercase {
  text-transform: uppercase;
}

td.bold {
  font-weight: bold;
  text-transform: uppercase;
}

td.dicePreview {
  font-size: 32px;
}

td.alt {
  font-size: 9px;
}

td.howToScore {
  font-size: 9px;
  text-transform: uppercase;
  padding: 0 10px;
}

td.arrow {
  font-size: 20px;
}

.fillFont {
  font-family: 'Gloria Hallelujah', cursive;
  color: darkblue;
}

/*backgroundstyle*/
.paper {
  display: block;
  padding: 20px 10px 10px 10px;
  position: relative;
  margin-bottom: 50px;
}

.paper:after {
  content: '';
  background-color: #fff;
  background-image: url("https://www.transparenttextures.com/patterns/cardboard.png");
  opacity: 0.7;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  position: absolute;
  z-index: -1;
}

@media only screen and (max-width: 600px) {
  .fiveDice .dice {
  width: 50px;
  height: 50px;
  line-height: 50px;
  }

  .fiveDice button {
  font-size: 50px;
  width: 32px;
  height: 60px;
  }
}

@media only screen and (min-width: 600px) {
  .fiveDice .dice {
  width: 80px;
  height: 80px;
  line-height: 80px;
  margin: 10px;
  }

  .fiveDice button {
  font-size: 80px;
  width: 60px;
  height: 80px;
  }
}

@media only screen and (min-width: 768px) {
}
</style>

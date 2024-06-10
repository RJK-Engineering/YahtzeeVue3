<script setup>
const props = defineProps(['frequency'])

import { ref, computed } from 'vue'

class Round {
    upperScores = []
    // upperScore
    // bonus
    // upperScoreTotal
    // threeOfKind
    // fourOfKind
    // fullHouse
    // smStraight
    // lgStraight
    // yahtzee
    // chance
    // lowerScore
    // upperScoreLower
    // grandTotal
}
const games = ref([1,2,3,4,5].map(() => new Round()))
const currentRoundNr = ref(0)
const currentRound = computed(() => games.value[currentRoundNr.value])

const upperScores = computed(() => {
    const scores = props.frequency.map((frequency, i) => frequency * (i+1))
    currentRound.value.upperScores = scores
    return games.value.map((round) => round.upperScores)
})
const upperScore = computed(() => {
    const score = currentRound.value.upperScores.reduce((acc, val) => acc + val)
    currentRound.value.upperScore = score
    return games.value.map((round) => round.upperScore)
})

const bonus = computed(() => {
    const score = upperScore.value[0] >= 63 ? 35 : 0
    return [score, 0, 0, 0, 0]
})
const upperScoreTotal = computed(() => {
    const score = upperScore.value[0] + bonus.value[0]
    return [score, 0, 0, 0, 0]
})
const threeOfKind = computed(() => {
    const counts = props.frequency.reduce((acc, val) => acc || val >= 3, false)
    const score = counts ? upperScores.value[0].reduce((acc, val) => acc + val) : 0
    return [score, 0, 0, 0, 0]
})
const fourOfKind = computed(() => {
    const counts = props.frequency.reduce((acc, val) => acc || val >= 4, false)
    const score = counts ? upperScores.value[0].reduce((acc, val) => acc + val) : 0
    return [score, 0, 0, 0, 0]
})
const fullHouse = computed(() => {
    const score = 0
    return [score, 0, 0, 0, 0]
})
const smStraight = computed(() => {
    const score = 0
    return [score, 0, 0, 0, 0]
})
const lgStraight = computed(() => {
    const score = 0
    return [score, 0, 0, 0, 0]
})
const yahtzee = computed(() => {
    const score = 0
    return [score, 0, 0, 0, 0]
})
const chance = computed(() => {
    const score = 0
    return [score, 0, 0, 0, 0]
})
const lowerScore = computed(() => {
    const score = 0
    return [score, 0, 0, 0, 0]
})
const upperScoreLower = computed(() => {
    const score = 0
    return [score, 0, 0, 0, 0]
})
const grandTotal = computed(() => {
    const score = 0
    return [score, 0, 0, 0, 0]
})
</script>

<template>
    <div class="paper">
        <table>
            <tr>
                <td class="noBorder"></td>
            </tr>
            <tr>
                <th class="title noBorder" colspan="7">scoreblok</th>
                <th class="title noBorder"><img class="posImg" src="../../public/dice.png"></th>
            </tr>
            <tr>
                <td class="noBorder"></td>
            </tr>
            <tr>
                <th class="h1 noBorder" colspan="2">deel 1</th>
                <th class="h1 noBorder">hoe te scoren</th>
                <th class="h2 noBorder">Spel 1</th>
                <th class="h2 noBorder">Spel 2</th>
                <th class="h2 noBorder">Spel 3</th>
                <th class="h2 noBorder">Spel 4</th>
                <th class="h2 noBorder">Spel 5</th>
            </tr>
            <tr>
                <td class="noBorderRight">enen</td>
                <td class="dicePreview noBorderLeft">&#x2680;</td>
                <td class="howToScore">waarde van alle enen</td>
                <td id="aces1" class="fillFont keepScore">{{ upperScores[0][0] }}</td>
                <td id="aces2" class="fillFont keepScore">{{ upperScores[1][0] }}</td>
                <td id="aces3" class="fillFont keepScore">{{ upperScores[2][0] }}</td>
                <td id="aces4" class="fillFont keepScore">{{ upperScores[3][0] }}</td>
                <td id="aces5" class="fillFont keepScore">{{ upperScores[4][0] }}</td>
            </tr>
            <tr>
                <td class="noBorderRight">tweeën</td>
                <td class="dicePreview noBorderLeft">&#x2681;</td>
                <td class="howToScore">waarde van alle tweeën</td>
                <td id="twos1" class="fillFont keepScore">{{ upperScores[0][1] }}</td>
                <td id="twos2" class="fillFont keepScore">{{ upperScores[1][1] }}</td>
                <td id="twos3" class="fillFont keepScore">{{ upperScores[2][1] }}</td>
                <td id="twos4" class="fillFont keepScore">{{ upperScores[3][1] }}</td>
                <td id="twos5" class="fillFont keepScore">{{ upperScores[4][1] }}</td>
            </tr>
            <tr>
                <td class="noBorderRight">drieën</td>
                <td class="dicePreview noBorderLeft">&#x2682;</td>
                <td class="howToScore">waarde van alle drieën</td>
                <td id="threes1" class="fillFont keepScore">{{ upperScores[0][2] }}</td>
                <td id="threes2" class="fillFont keepScore">{{ upperScores[1][2] }}</td>
                <td id="threes3" class="fillFont keepScore">{{ upperScores[2][2] }}</td>
                <td id="threes4" class="fillFont keepScore">{{ upperScores[3][2] }}</td>
                <td id="threes5" class="fillFont keepScore">{{ upperScores[4][2] }}</td>
            </tr>
            <tr>
                <td class="noBorderRight">vieren</td>
                <td class="dicePreview noBorderLeft">&#x2683;</td>
                <td class="howToScore">waarde van alle vieren</td>
                <td id="fours1" class="fillFont keepScore">{{ upperScores[0][3] }}</td>
                <td id="fours2" class="fillFont keepScore">{{ upperScores[1][3] }}</td>
                <td id="fours3" class="fillFont keepScore">{{ upperScores[2][3] }}</td>
                <td id="fours4" class="fillFont keepScore">{{ upperScores[3][3] }}</td>
                <td id="fours5" class="fillFont keepScore">{{ upperScores[4][3] }}</td>
            </tr>
            <tr>
                <td class="noBorderRight">vijven</td>
                <td class="dicePreview noBorderLeft">&#x2684;</td>
                <td class="howToScore">waarde van alle vijven</td>
                <td id="fives1" class="fillFont keepScore">{{ upperScores[0][4] }}</td>
                <td id="fives2" class="fillFont keepScore">{{ upperScores[1][4] }}</td>
                <td id="fives3" class="fillFont keepScore">{{ upperScores[2][4] }}</td>
                <td id="fives4" class="fillFont keepScore">{{ upperScores[3][4] }}</td>
                <td id="fives5" class="fillFont keepScore">{{ upperScores[4][4] }}</td>
            </tr>
            <tr>
                <td class="noBorderRight">zessen</td>
                <td class="dicePreview noBorderLeft">&#x2685;</td>
                <td class="howToScore">waarde van alle zessen</td>
                <td id="sixes1" class="fillFont keepScore">{{ upperScores[0][5] }}</td>
                <td id="sixes2" class="fillFont keepScore">{{ upperScores[1][5] }}</td>
                <td id="sixes3" class="fillFont keepScore">{{ upperScores[2][5] }}</td>
                <td id="sixes4" class="fillFont keepScore">{{ upperScores[3][5] }}</td>
                <td id="sixes5" class="fillFont keepScore">{{ upperScores[4][5] }}</td>
            </tr>
            <tr id="total">
                <td class="uppercase" colspan="2">totaal</td>
                <td class="arrow">&#10132;</td>
                <td id="upperScore1" class="fillFont">{{ upperScore[0] }}</td>
                <td id="upperScore2" class="fillFont">{{ upperScore[1] }}</td>
                <td id="upperScore3" class="fillFont">{{ upperScore[2] }}</td>
                <td id="upperScore4" class="fillFont">{{ upperScore[3] }}</td>
                <td id="upperScore5" class="fillFont">{{ upperScore[4] }}</td>
            </tr>
            <tr id="bonus">
                <td class="noBorderRight">bonus</td>
                <td class="alt noBorderLeft">als totaal 63<br>of meer is</td>
                <td class="howToScore">35 punten</td>
                <td id="bonus1" class="fillFont">{{ bonus[0] }}</td>
                <td id="bonus2" class="fillFont">{{ bonus[1] }}</td>
                <td id="bonus3" class="fillFont">{{ bonus[2] }}</td>
                <td id="bonus4" class="fillFont">{{ bonus[3] }}</td>
                <td id="bonus5" class="fillFont">{{ bonus[4] }}</td>
            </tr>
            <tr id="upperTotal">
                <td class="uppercase noBorderRight">totaal</td>
                <td class="alt uppercase noBorderLeft">van de<br>bovenste<br>helft</td>
                <td class="arrow">&#10132;</td>
                <td id="totalUpperScore1" class="fillFont">{{ upperScoreTotal[0] }}</td>
                <td id="totalUpperScore2" class="fillFont">{{ upperScoreTotal[1] }}</td>
                <td id="totalUpperScore3" class="fillFont">{{ upperScoreTotal[2] }}</td>
                <td id="totalUpperScore4" class="fillFont">{{ upperScoreTotal[3] }}</td>
                <td id="totalUpperScore5" class="fillFont">{{ upperScoreTotal[4] }}</td>
            </tr>
            <tr>
                <th class="h1 noBorder" colspan="2">deel 2</th>
            </tr>

            <tr>
                <td colspan="2">3 of a kind</td>
                <td class="howToScore">totaal van alle dobbelstenen</td>
                <td id="threeOfKind1" class="fillFont keepScore">{{ threeOfKind[0] }}</td>
                <td id="threeOfKind2" class="fillFont keepScore">{{ threeOfKind[1] }}</td>
                <td id="threeOfKind3" class="fillFont keepScore">{{ threeOfKind[2] }}</td>
                <td id="threeOfKind4" class="fillFont keepScore">{{ threeOfKind[3] }}</td>
                <td id="threeOfKind5" class="fillFont keepScore">{{ threeOfKind[4] }}</td>
            </tr>
            <tr>
                <td colspan="2">4 of a kind</td>
                <td class="howToScore">totaal van alle dobbelstenen</td>
                <td id="fourOfKind1" class="fillFont keepScore">{{ fourOfKind[0] }}</td>
                <td id="fourOfKind2" class="fillFont keepScore">{{ fourOfKind[1] }}</td>
                <td id="fourOfKind3" class="fillFont keepScore">{{ fourOfKind[2] }}</td>
                <td id="fourOfKind4" class="fillFont keepScore">{{ fourOfKind[3] }}</td>
                <td id="fourOfKind5" class="fillFont keepScore">{{ fourOfKind[4] }}</td>
            </tr>
            <tr>
                <td colspan="2">full house</td>
                <td class="howToScore">25 punten</td>
                <td id="fullHouse1" class="fillFont keepScore">{{ fullHouse[0] }}</td>
                <td id="fullHouse2" class="fillFont keepScore">{{ fullHouse[1] }}</td>
                <td id="fullHouse3" class="fillFont keepScore">{{ fullHouse[2] }}</td>
                <td id="fullHouse4" class="fillFont keepScore">{{ fullHouse[3] }}</td>
                <td id="fullHouse5" class="fillFont keepScore">{{ fullHouse[4] }}</td>
            </tr>
            <tr>
                <td class="noBorderRight">kleine straat</td>
                <td class="alt noBorderLeft">4<br>opeenvolgende nummers</td>
                <td class="howToScore">30 punten</td>
                <td id="smStraight1" class="fillFont keepScore">{{ smStraight[0] }}</td>
                <td id="smStraight2" class="fillFont keepScore">{{ smStraight[1] }}</td>
                <td id="smStraight3" class="fillFont keepScore">{{ smStraight[2] }}</td>
                <td id="smStraight4" class="fillFont keepScore">{{ smStraight[3] }}</td>
                <td id="smStraight5" class="fillFont keepScore">{{ smStraight[4] }}</td>
            </tr>
            <tr>
                <td class="noBorderRight">grote straat</td>
                <td class="alt noBorderLeft">5<br>opeenvolgende nummers</td>
                <td class="howToScore">40 punten</td>
                <td id="lgStraight1" class="fillFont keepScore">{{ lgStraight[0] }}</td>
                <td id="lgStraight2" class="fillFont keepScore">{{ lgStraight[1] }}</td>
                <td id="lgStraight3" class="fillFont keepScore">{{ lgStraight[2] }}</td>
                <td id="lgStraight4" class="fillFont keepScore">{{ lgStraight[3] }}</td>
                <td id="lgStraight5" class="fillFont keepScore">{{ lgStraight[4] }}</td>
            </tr>
            <tr>
                <td class="noBorderRight">yahtzee</td>
                <td class="alt noBorderLeft">5<br>dezelfde<br>nummers</td>
                <td class="howToScore">50 punten</td>
                <td id="yahtzee1" class="fillFont keepScore">{{ yahtzee[0] }}</td>
                <td id="yahtzee2" class="fillFont keepScore">{{ yahtzee[1] }}</td>
                <td id="yahtzee3" class="fillFont keepScore">{{ yahtzee[2] }}</td>
                <td id="yahtzee4" class="fillFont keepScore">{{ yahtzee[3] }}</td>
                <td id="yahtzee5" class="fillFont keepScore">{{ yahtzee[4] }}</td>
            </tr>
            <tr id="chance">
                <td colspan="2">chance</td>
                <td class="howToScore">totaal van alle dobbelstenen</td>
                <td id="chance1" class="fillFont keepScore">{{ chance[0] }}</td>
                <td id="chance2" class="fillFont keepScore">{{ chance[1] }}</td>
                <td id="chance3" class="fillFont keepScore">{{ chance[2] }}</td>
                <td id="chance4" class="fillFont keepScore">{{ chance[3] }}</td>
                <td id="chance5" class="fillFont keepScore">{{ chance[4] }}</td>
            </tr>
            <tr id="lowerTotal">
                <td class="uppercase noBorderRight">totaal</td>
                <td class="alt uppercase noBorderLeft">van de<br>onderste<br>helft</td>
                <td class="arrow">&#10132;</td>
                <td id="lowerScore1" class="fillFont">{{ lowerScore[0] }}</td>
                <td id="lowerScore2" class="fillFont">{{ lowerScore[1] }}</td>
                <td id="lowerScore3" class="fillFont">{{ lowerScore[2] }}</td>
                <td id="lowerScore4" class="fillFont">{{ lowerScore[3] }}</td>
                <td id="lowerScore5" class="fillFont">{{ lowerScore[4] }}</td>
            </tr>
            <tr id="lowUpperTotal">
                <td class="uppercase noBorderRight">totaal</td>
                <td class="alt uppercase noBorderLeft">van de<br>bovenste<br>helft</td>
                <td class="arrow">&#10132;</td>
                <td id="upperScoreLower1" class="fillFont">{{ upperScoreLower[0] }}</td>
                <td id="upperScoreLower2" class="fillFont">{{ upperScoreLower[1] }}</td>
                <td id="upperScoreLower3" class="fillFont">{{ upperScoreLower[2] }}</td>
                <td id="upperScoreLower4" class="fillFont">{{ upperScoreLower[3] }}</td>
                <td id="upperScoreLower5" class="fillFont">{{ upperScoreLower[4] }}</td>
            </tr>
            <tr id="grandTotal">
                <td class="bold" colspan="2">totaal generaal</td>
                <td class="arrow">&#10132;</td>
                <td id="grandTotal1" class="fillFont">{{ grandTotal[0] }}</td>
                <td id="grandTotal2" class="fillFont">{{ grandTotal[1] }}</td>
                <td id="grandTotal3" class="fillFont">{{ grandTotal[2] }}</td>
                <td id="grandTotal4" class="fillFont">{{ grandTotal[3] }}</td>
                <td id="grandTotal5" class="fillFont">{{ grandTotal[4] }}</td>
            </tr>
        </table>
    </div>
</template>

<script setup>
const props = defineProps(['diceModel'])

import { computed } from 'vue'

const round = { aces: '', twos: '', threes: '', fours: '', fives: '', sixes: '' }
const scores = computed(() => {
    return [{
        aces: props.diceModel[0],
        twos: props.diceModel[1] * 2,
        threes: props.diceModel[2] * 3,
        fours: props.diceModel[3] * 4,
        fives: props.diceModel[4] * 5,
        sixes: props.diceModel[5] * 6,
    }, round, round, round, round]
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
                <td id="aces1" class="fillFont keepScore">{{ scores[0].aces }}</td>
                <td id="aces2" class="fillFont keepScore">{{ scores[1].aces }}</td>
                <td id="aces3" class="fillFont keepScore">{{ scores[2].aces }}</td>
                <td id="aces4" class="fillFont keepScore">{{ scores[3].aces }}</td>
                <td id="aces5" class="fillFont keepScore">{{ scores[4].aces }}</td>
            </tr>
            <tr>
                <td class="noBorderRight">tweeën</td>
                <td class="dicePreview noBorderLeft">&#x2681;</td>
                <td class="howToScore">waarde van alle tweeën</td>
                <td id="twos1" class="fillFont keepScore">{{ scores[0].twos }}</td>
                <td id="twos2" class="fillFont keepScore">{{ scores[1].twos }}</td>
                <td id="twos3" class="fillFont keepScore">{{ scores[2].twos }}</td>
                <td id="twos4" class="fillFont keepScore">{{ scores[3].twos }}</td>
                <td id="twos5" class="fillFont keepScore">{{ scores[4].twos }}</td>
            </tr>
            <tr>
                <td class="noBorderRight">drieën</td>
                <td class="dicePreview noBorderLeft">&#x2682;</td>
                <td class="howToScore">waarde van alle drieën</td>
                <td id="threes1" class="fillFont keepScore">{{ scores[0].threes }}</td>
                <td id="threes2" class="fillFont keepScore">{{ scores[1].threes }}</td>
                <td id="threes3" class="fillFont keepScore">{{ scores[2].threes }}</td>
                <td id="threes4" class="fillFont keepScore">{{ scores[3].threes }}</td>
                <td id="threes5" class="fillFont keepScore">{{ scores[4].threes }}</td>
            </tr>
            <tr>
                <td class="noBorderRight">vieren</td>
                <td class="dicePreview noBorderLeft">&#x2683;</td>
                <td class="howToScore">waarde van alle vieren</td>
                <td id="fours1" class="fillFont keepScore">{{ scores[0].fours }}</td>
                <td id="fours2" class="fillFont keepScore">{{ scores[1].fours }}</td>
                <td id="fours3" class="fillFont keepScore">{{ scores[2].fours }}</td>
                <td id="fours4" class="fillFont keepScore">{{ scores[3].fours }}</td>
                <td id="fours5" class="fillFont keepScore">{{ scores[4].fours }}</td>
            </tr>
            <tr>
                <td class="noBorderRight">vijven</td>
                <td class="dicePreview noBorderLeft">&#x2684;</td>
                <td class="howToScore">waarde van alle vijven</td>
                <td id="fives1" class="fillFont keepScore">{{ scores[0].fives }}</td>
                <td id="fives2" class="fillFont keepScore">{{ scores[1].fives }}</td>
                <td id="fives3" class="fillFont keepScore">{{ scores[2].fives }}</td>
                <td id="fives4" class="fillFont keepScore">{{ scores[3].fives }}</td>
                <td id="fives5" class="fillFont keepScore">{{ scores[4].fives }}</td>
            </tr>
            <tr>
                <td class="noBorderRight">zessen</td>
                <td class="dicePreview noBorderLeft">&#x2685;</td>
                <td class="howToScore">waarde van alle zessen</td>
                <td id="sixes1" class="fillFont keepScore">{{ scores[0].sixes }}</td>
                <td id="sixes2" class="fillFont keepScore">{{ scores[1].sixes }}</td>
                <td id="sixes3" class="fillFont keepScore">{{ scores[2].sixes }}</td>
                <td id="sixes4" class="fillFont keepScore">{{ scores[3].sixes }}</td>
                <td id="sixes5" class="fillFont keepScore">{{ scores[4].sixes }}</td>
            </tr>
            <tr id="total">
                <td class="uppercase" colspan="2">totaal</td>
                <td class="arrow">&#10132;</td>
                <td id="upperScore1" class="fillFont">{{ scores[0].upperScore }}</td>
                <td id="upperScore2" class="fillFont">{{ scores[1].upperScore }}</td>
                <td id="upperScore3" class="fillFont">{{ scores[2].upperScore }}</td>
                <td id="upperScore4" class="fillFont">{{ scores[3].upperScore }}</td>
                <td id="upperScore5" class="fillFont">{{ scores[4].upperScore }}</td>
            </tr>
            <tr id="bonus">
                <td class="noBorderRight">bonus</td>
                <td class="alt noBorderLeft">als totaal 63<br>of meer is</td>
                <td class="howToScore">35 punten</td>
                <td id="bonus1" class="fillFont">{{ scores[0].bonus }}</td>
                <td id="bonus2" class="fillFont">{{ scores[1].bonus }}</td>
                <td id="bonus3" class="fillFont">{{ scores[2].bonus }}</td>
                <td id="bonus4" class="fillFont">{{ scores[3].bonus }}</td>
                <td id="bonus5" class="fillFont">{{ scores[4].bonus }}</td>
            </tr>
            <tr id="upperTotal">
                <td class="uppercase noBorderRight">totaal</td>
                <td class="alt uppercase noBorderLeft">van de<br>bovenste<br>helft</td>
                <td class="arrow">&#10132;</td>
                <td id="totalUpperScore1" class="fillFont">{{ scores[0].totalUpperScore }}</td>
                <td id="totalUpperScore2" class="fillFont">{{ scores[1].totalUpperScore }}</td>
                <td id="totalUpperScore3" class="fillFont">{{ scores[2].totalUpperScore }}</td>
                <td id="totalUpperScore4" class="fillFont">{{ scores[3].totalUpperScore }}</td>
                <td id="totalUpperScore5" class="fillFont">{{ scores[4].totalUpperScore }}</td>
            </tr>
            <tr>
                <th class="h1 noBorder" colspan="2">deel 2</th>
            </tr>

            <tr>
                <td colspan="2">3 of a kind</td>
                <td class="howToScore">totaal van alle dobbelstenen</td>
                <td id="threeOfKind1" class="fillFont keepScore">{{ scores[0].threeOfKind }}</td>
                <td id="threeOfKind2" class="fillFont keepScore">{{ scores[1].threeOfKind }}</td>
                <td id="threeOfKind3" class="fillFont keepScore">{{ scores[2].threeOfKind }}</td>
                <td id="threeOfKind4" class="fillFont keepScore">{{ scores[3].threeOfKind }}</td>
                <td id="threeOfKind5" class="fillFont keepScore">{{ scores[4].threeOfKind }}</td>
            </tr>
            <tr>
                <td colspan="2">4 of a kind</td>
                <td class="howToScore">totaal van alle dobbelstenen</td>
                <td id="fourOfKind1" class="fillFont keepScore">{{ scores[0].fourOfKind }}</td>
                <td id="fourOfKind2" class="fillFont keepScore">{{ scores[1].fourOfKind }}</td>
                <td id="fourOfKind3" class="fillFont keepScore">{{ scores[2].fourOfKind }}</td>
                <td id="fourOfKind4" class="fillFont keepScore">{{ scores[3].fourOfKind }}</td>
                <td id="fourOfKind5" class="fillFont keepScore">{{ scores[4].fourOfKind }}</td>
            </tr>
            <tr>
                <td colspan="2">full house</td>
                <td class="howToScore">25 punten</td>
                <td id="fullHouse1" class="fillFont keepScore">{{ scores[0].fullHouse }}</td>
                <td id="fullHouse2" class="fillFont keepScore">{{ scores[1].fullHouse }}</td>
                <td id="fullHouse3" class="fillFont keepScore">{{ scores[2].fullHouse }}</td>
                <td id="fullHouse4" class="fillFont keepScore">{{ scores[3].fullHouse }}</td>
                <td id="fullHouse5" class="fillFont keepScore">{{ scores[4].fullHouse }}</td>
            </tr>
            <tr>
                <td class="noBorderRight">kleine straat</td>
                <td class="alt noBorderLeft">4<br>opeenvolgende nummers</td>
                <td class="howToScore">30 punten</td>
                <td id="smStraight1" class="fillFont keepScore">{{ scores[0].smStraight }}</td>
                <td id="smStraight2" class="fillFont keepScore">{{ scores[1].smStraight }}</td>
                <td id="smStraight3" class="fillFont keepScore">{{ scores[2].smStraight }}</td>
                <td id="smStraight4" class="fillFont keepScore">{{ scores[3].smStraight }}</td>
                <td id="smStraight5" class="fillFont keepScore">{{ scores[4].smStraight }}</td>
            </tr>
            <tr>
                <td class="noBorderRight">grote straat</td>
                <td class="alt noBorderLeft">5<br>opeenvolgende nummers</td>
                <td class="howToScore">40 punten</td>
                <td id="lgStraight1" class="fillFont keepScore">{{ scores[0].lgStraight }}</td>
                <td id="lgStraight2" class="fillFont keepScore">{{ scores[1].lgStraight }}</td>
                <td id="lgStraight3" class="fillFont keepScore">{{ scores[2].lgStraight }}</td>
                <td id="lgStraight4" class="fillFont keepScore">{{ scores[3].lgStraight }}</td>
                <td id="lgStraight5" class="fillFont keepScore">{{ scores[4].lgStraight }}</td>
            </tr>
            <tr>
                <td class="noBorderRight">yahtzee</td>
                <td class="alt noBorderLeft">5<br>dezelfde<br>nummers</td>
                <td class="howToScore">50 punten</td>
                <td id="yahtzee1" class="fillFont keepScore">{{ scores[0].yahtzee }}</td>
                <td id="yahtzee2" class="fillFont keepScore">{{ scores[1].yahtzee }}</td>
                <td id="yahtzee3" class="fillFont keepScore">{{ scores[2].yahtzee }}</td>
                <td id="yahtzee4" class="fillFont keepScore">{{ scores[3].yahtzee }}</td>
                <td id="yahtzee5" class="fillFont keepScore">{{ scores[4].yahtzee }}</td>
            </tr>
            <tr id="chance">
                <td colspan="2">chance</td>
                <td class="howToScore">totaal van alle dobbelstenen</td>
                <td id="chance1" class="fillFont keepScore">{{ scores[0].chance }}</td>
                <td id="chance2" class="fillFont keepScore">{{ scores[1].chance }}</td>
                <td id="chance3" class="fillFont keepScore">{{ scores[2].chance }}</td>
                <td id="chance4" class="fillFont keepScore">{{ scores[3].chance }}</td>
                <td id="chance5" class="fillFont keepScore">{{ scores[4].chance }}</td>
            </tr>
            <tr id="lowerTotal">
                <td class="uppercase noBorderRight">totaal</td>
                <td class="alt uppercase noBorderLeft">van de<br>onderste<br>helft</td>
                <td class="arrow">&#10132;</td>
                <td id="lowerScore1" class="fillFont">{{ scores[0].lowerScore }}</td>
                <td id="lowerScore2" class="fillFont">{{ scores[1].lowerScore }}</td>
                <td id="lowerScore3" class="fillFont">{{ scores[2].lowerScore }}</td>
                <td id="lowerScore4" class="fillFont">{{ scores[3].lowerScore }}</td>
                <td id="lowerScore5" class="fillFont">{{ scores[4].lowerScore }}</td>
            </tr>
            <tr id="lowUpperTotal">
                <td class="uppercase noBorderRight">totaal</td>
                <td class="alt uppercase noBorderLeft">van de<br>bovenste<br>helft</td>
                <td class="arrow">&#10132;</td>
                <td id="upperScoreLower1" class="fillFont">{{ scores[0].upperScoreLower }}</td>
                <td id="upperScoreLower2" class="fillFont">{{ scores[1].upperScoreLower }}</td>
                <td id="upperScoreLower3" class="fillFont">{{ scores[2].upperScoreLower }}</td>
                <td id="upperScoreLower4" class="fillFont">{{ scores[3].upperScoreLower }}</td>
                <td id="upperScoreLower5" class="fillFont">{{ scores[4].upperScoreLower }}</td>
            </tr>
            <tr id="grandTotal">
                <td class="bold" colspan="2">totaal generaal</td>
                <td class="arrow">&#10132;</td>
                <td id="grandTotal1" class="fillFont">{{ scores[0].grandTotal }}</td>
                <td id="grandTotal2" class="fillFont">{{ scores[1].grandTotal }}</td>
                <td id="grandTotal3" class="fillFont">{{ scores[2].grandTotal }}</td>
                <td id="grandTotal4" class="fillFont">{{ scores[3].grandTotal }}</td>
                <td id="grandTotal5" class="fillFont">{{ scores[4].grandTotal }}</td>
            </tr>
        </table>
    </div>
</template>

<template>
    <div>
        <div class="xcont">
            <div class="md-layout">
                <div class="md-layout-item md-size-5"></div>
                <div class="md-layout-item">
                    <div class="md-layout">
                        <team-inputs :teamName="'Team A'" :tradePicks="teamAPicks" @update-traded-picks="updateTeamATradedPicks"></team-inputs>

                        <team-inputs :teamName="'Team B'" :tradePicks="teamBPicks"  @update-traded-picks="updateTeamBTradedPicks"></team-inputs>
                    </div>
                </div>
                <div class="md-layout-item md-size-5"></div>
            </div>
        </div>
        <div class="xcont">
            <div class="md-layout">
                <div class="md-layout-item md-size-5"></div>
                 <div class="md-layout-item">
                        <md-card class="evaluation-card">
                            <md-card-content>
                                <button class="md-button md-raised eval-button" @click="evaluateTrade">
                                    <md-icon  style="color:white;font:bold;" >play_arrow</md-icon><span> Evaluate Trade</span>
                                </button>
                            </md-card-content>
                        </md-card>
                </div>
                <div class="md-layout-item md-size-5"></div>
            </div>
        </div>
        <div class="xcont">
            <evaluate></evaluate>
        </div>
    </div>
</template>

<script>
//import Vue from 'vue';
import TeamInputs from './TeamInputs.vue';
import Evaluate from './Evaluate.vue';

//Vue.component('team-inputs', TeamInputs);
//Vue.component('evaluate', Evaluate);

export default 
    {
        name: 'CalculationForm',
        components: { 
            'team-inputs': TeamInputs, 
            'evaluate': Evaluate 
        },
        props: {
            draftPicks: {required: true, type: Array}
        },
        data() {
            return {
                teamAValue: 0,
                teamAPicks: ["", ""],
                teambBValue: 0,
                teamBPicks: ["", ""]
            }
        },
        methods: {
            updateTeamATradedPicks: function(picks) {
                this.$data.teamAPicks = picks;
            },
            updateTeamBTradedPicks: function(picks) {
                this.$data.teamBPicks = picks;
            },
            evaluateTrade: function() {
                let teamAVal = 0;
                let teamBVal = 0;
                const pickData = this.$props.draftPicks;
                this.$data.teamAPicks.forEach(el => {
                    if (!(el==="")){
                        if (el > pickData.length) {
                            teamAVal += 1;
                        } else {
                            let p = pickData[el];
                            teamAVal += p.value;
                        }
                    }
                });
                this.$data.teamBPicks.forEach(el => {
                    if (!(el === "")) {
                        if (el > pickData.length) {
                            teamBVal += 1;
                        } else {
                            let p = pickData[el];
                            teamBVal += p.value;
                        }
                    }
                });
                this.$data.teamAValue = teamAVal;
                this.$data.teamBValue = teamBVal;
            }
        }
    };
</script>
<style scoped>
.evaluation-card {
        min-height: 100px;
    }
    .eval-button{
        color: white;
        text-align: center;
        background-color: #1AA260;
        min-width: 180px;
    }
</style>
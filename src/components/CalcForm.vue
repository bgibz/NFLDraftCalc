<template>
    <div>
        <div class="xcont">
            <div class="md-layout">
                <div class="md-layout-item md-size-5"></div>
                <div class="md-layout-item">
                    <div class="md-layout">
                        <team-inputs :teamName="'Team A'" :tradePicks.sync="teamAPicks" @update-traded-picks="updateTeamATradedPicks" ></team-inputs>

                        <team-inputs :teamName="'Team B'" :tradePicks.sync="teamBPicks"  @update-traded-picks="updateTeamBTradedPicks" ></team-inputs>
                    </div>
                </div>
                <div class="md-layout-item md-size-5"></div>
            </div>
        </div>
        <div class="xcont">
            <evaluate :display="displayCalc" :teamAValue="teamAValue" :teamBValue="teamBValue" :diff="difference"></evaluate>
        </div>

        <div class="xcont">
            <div class="md-layout">
                <div class="md-layout-item"></div>
                 <div class="md-layout-item">
                        <!--<md-card class="evaluation-card">
                            <md-card-content>-->
                                <button class="md-button md-raised eval-button" @click="evaluateTrade">
                                    <md-icon  style="color:white;font:bold;" >play_arrow</md-icon><span> Evaluate Trade</span>
                                </button>
                            <!--</md-card-content>
                        </md-card>-->
                </div>
                <div class="md-layout">
                    <div class="md-layout-item">
                        <button class="md-button md-raised reset-button" @click="resetCalc">
                                <md-icon  style="color:white;font:bold;" >restart_alt</md-icon><span> Reset</span>
                        </button>
                    </div>
                </div>
                <div class="md-layout-item"></div>
            </div>
        </div>
        
    </div>
</template>

<script>
import Vue from 'vue';
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
                teamBValue: 0,
                teamBPicks: ["", ""],
                displayCalc: false,
                difference: 0
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
                            let p = pickData[el - 1];
                            teamAVal += p.value;
                        }
                    }
                });
                this.$data.teamBPicks.forEach(el => {
                    if (!(el === "")) {
                        if (el > pickData.length) {
                            teamBVal += 1;
                        } else {
                            let p = pickData[el - 1];
                            teamBVal += p.value;
                        }
                    }
                });
                this.teamAValue = teamAVal;
                this.teamBValue = teamBVal;
                this.difference = teamAVal - teamBVal;
                this.displayCalc = true;
            },
            resetCalc: function() {
                this.teamAPicks.splice(2);
                this.teamBPicks.splice(2);
                Vue.set(this.teamAPicks, 0, "");
                Vue.set(this.teamAPicks, 1, "");
                Vue.set(this.teamBPicks, 0, "");
                Vue.set(this.teamBPicks, 1, "");
                this.teamAValue = 0;
                this.teamBValue= 0,
                this.difference = 0;
                this.displayCalc = false;
            }
        }
    };
</script>
<style scoped>
.evaluation-card {
        min-height: 100px;
    }
    .eval-button { 
        color: white;
        text-align: center;
        background-color: #1AA260;
        min-width: 180px;
    }
    .reset-button {
        color: white;
        text-align: center;
        background-color: #de5246;
        min-width: 180px;
    }
</style>
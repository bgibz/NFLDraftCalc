<template>
    <div>
        <div class="xcont">
            <div class="md-layout">
                <div class="md-layout-item md-size-5"></div>
                <div class="md-layout-item">
                    <div class="md-layout">
                        <team-inputs :teamName="'Team A'" :tradePicks="teamAPicks"></team-inputs>

                        <team-inputs :teamName="'Team B'" :tradePicks="teamBPicks"></team-inputs>
                    </div>
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
        data() {
            return {
            teamAPicks: ["", ""],
            teamBPicks: ["", ""]
            }
        }
    };
</script>
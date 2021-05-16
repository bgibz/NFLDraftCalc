<template>
    <div>
        <div class="xcont">
            <div class="md-layout">
                <div class="md-layout-item md-size-5"></div>
                <div class="md-layout-item">
                    <div class="md-layout">
                        <team-inputs :teamName="'Team A'"></team-inputs>

                        <team-inputs :teamName="'Team B'"></team-inputs>
                    </div>
                </div>
                <div class="md-layout-item md-size-5"></div>
            </div>
        </div>
        <div class="xcont">
            <div class="md-layout">
                <div class="md-layout-item md-size-5"></div>
                <div class="md-layout-item">
                    <md-card>
                    Trade gets evaluated here
                    </md-card>
                </div>
                <div class="md-layout-item md-size-5"></div>
            </div>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import TeamInputs from './TeamInputs.vue';

Vue.component('team-inputs', TeamInputs);

export default 
    {
        name: 'CalculationForm',
        components: { TeamInputs }
    };
</script>
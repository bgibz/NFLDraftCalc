<template>
    <div class="md-layout">
        <div class="md-layout-item md-size-5"></div>
        <div class="md-layout-item">
            <div class="md-layout">
            <md-card class="md-layout-item">
                <md-card-header>
                    <div class="md-title">Team A</div>
                </md-card-header>
                <md-card-content>
                    <div class="md-layout md-gutter">
                        <div class="md-layout-item">
                            <md-field>
                            <label for="Adraft1">Draft Pick To Trade</label>
                            <md-input name="Adraft1" id="Adraft1" v-model="ATeamDraft"/>
                            </md-field>
                            <md-field>
                            <label for="Adraft1">Draft Pick To Trade</label>
                            <md-input name="Adraft1" id="Adraft1" v-model="ATeamDraft"/>
                            </md-field>
                            <md-field>
                            <label for="Adraft1">Draft Pick To Trade</label>
                            <md-input name="Adraft1" id="Adraft1" v-model="ATeamDraft"/>
                            </md-field>
                            <md-button class="md-icon-button md-raised md-primary">
                            <md-icon>add</md-icon>
                            </md-button>
                        </div>
                    </div>
                </md-card-content>
            </md-card>
                <team-inputs :teamName="'Team B'"></team-inputs>
        </div>
        </div>
        <div class="md-layout-item md-size-5"></div>
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
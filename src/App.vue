<template>
  <div id="app">
    <md-app id="calc-app">
      <md-app-toolbar class="md-primary">
          <span class="md-title">NFL Draft Pick Trade Calculator</span>
        </md-app-toolbar>

      <md-app-content>
        <calc-form :draftPicks="$options.picks"></calc-form>
      </md-app-content>

    </md-app>
    <div class="xcont">
      <div class="md-layout draft-chart">
        <div class="md-layout-item md-size-10"></div>
        <div class="md-layout-item">
          <draft-chart :numRounds=7 :draftRounds="$options.rounds" :draftPicks="$options.picks" :year="$options.year"></draft-chart>
        </div>
        <div class="md-layout-item md-size-10"></div>
      </div>
    </div>
  </div>
</template>

<script>
import Vue from 'vue';
import jimmy from '../public/resources/jimmy.json';
import DraftChart from './components/DraftChart.vue';
import CalcForm from './components/CalcForm.vue';

Vue.component('draft-chart', DraftChart);
Vue.component('calc-form', CalcForm);

export default {
  components: { DraftChart },
  name: 'App',
  numRounds: jimmy.numRounds,
  rounds: jimmy.rounds,
  picks: jimmy.draftPicks,
  year: jimmy.year
};
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Material+Icons");
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  background: #E0E0E0;
}
#calc-app{
  background: #E0E0E0
}
.xcont {
        padding: 5px 0px 5px 0px;
    }
</style>

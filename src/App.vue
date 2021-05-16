<template>
  <div>
    <md-app id="app">
      <md-app-toolbar class="md-primary">
          <span class="md-title">NFL Draft Pick Trade Calculator</span>
        </md-app-toolbar>

      <md-app-content>
        <calc-form></calc-form>
      </md-app-content>

    </md-app>
    <div class="md-layout draft-chart">
      <div class="md-layout-item md-size-10"></div>
      <div class="md-layout-item">
        <draft-chart :numRounds=7 :draftRounds="$options.rounds" :draftPicks="$options.picks" :year="$options.year"></draft-chart>
      </div>
      <div class="md-layout-item md-size-10"></div>
    </div>
  </div>
</template>

<script>
import Vue from 'vue';
import jimmy from '../public/resources/jimmy.json';
import DraftChart from './components/DraftChart.vue';
import CalcForm from './components/CalcForm.vue';
/*
import VueMaterial from 'vue-material';
import 'vue-material/dist/vue-material.min.css';
import 'vue-material/dist/theme/default.css';
Vue.use(VueMaterial);
//Vue.use(MdApp);
//Vue.use(MdLayout);
//Vue.use(MdTitle);
*/
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
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
@import url("https://fonts.googleapis.com/css?family=Material+Icons");
</style>

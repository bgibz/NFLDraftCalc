<template>
  <md-app id="app">
    <md-app-toolbar class="md-primary">
        <span class="md-title">NFL Draft Pick Trade Calculator</span>
      </md-app-toolbar>

    <md-app-content>
    <div class="md-layout">Calc form goes here</div>
    </md-app-content>

    <md-app-drawer>
    <div class="md-layout">
      <div class="md-layout-item md-size-15"></div>
      <div class="md-layout-item">
        <draft-chart :numRounds=7 :draftRounds="$options.rounds" :draftPicks="$options.picks" :year="$options.year"></draft-chart>
      </div>
      <div class="md-layout-item md-size-15"></div>
    </div>
    </md-app-drawer>

  </md-app>
</template>

<script>
import Vue from 'vue';
import jimmy from '../public/resources/jimmy.json';
import DraftChart from './components/DraftChart.vue';
import { MdApp, MdLayout } from 'vue-material/dist/components';
import 'vue-material/dist/vue-material.min.css';
import 'vue-material/dist/theme/default.css';
Vue.use(MdApp);
Vue.use(MdLayout);

Vue.component('draft-chart', DraftChart);

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
</style>

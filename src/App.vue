<template>
  <div id="app">
    <draft-chart :numRounds=7 :draftRounds="$options.rounds" :draftPicks="$options.picks"></draft-chart>
  </div>
</template>

<script>
import jimmy from '../public/resources/jimmy.json'
import DraftChart from './components/DraftChart.vue';
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

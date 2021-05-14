<template>
    <md-card>
        <md-card-header>
            <div class="md-title">{{this.year}} Draft Chart</div>
        </md-card-header>
        <md-card-content>
            <md-table>
                <md-table-row>
                    <md-table-head v-for="n in numRounds" v-bind:key="n">
                        Round {{n}}
                    </md-table-head>
                </md-table-row>
                <md-table-row class="draftBody">
                        <md-table-cell v-for="round in draftRounds" v-bind:key="round.round">
                            <draft-round :round="round" :draftPicks="draftPicks" />
                        </md-table-cell>
                </md-table-row>
            </md-table>
        </md-card-content>
    </md-card> 
</template>
<script>
  import Vue from 'vue';
  import DraftRound from './DraftRound.vue';
  import { MdTable, MdCard } from 'vue-material/dist/components';
  import 'vue-material/dist/vue-material.min.css'
  import 'vue-material/dist/theme/default.css'
  Vue.use(MdTable);
  Vue.use(MdCard);

  Vue.component('draft-round', DraftRound);


  export default {
  components: { DraftRound },
      props: {
            numRounds: { default: 7, type: Number },
            draftRounds: { required: true, type: Array },
            draftPicks: { required: true, type: Array },
            year: {required: true, type: Array }
        },
        /*
        data() {
            return {
                numRounds: this.rounds,
                draftRounds: this.draftRounds,
                draftPicks: this.draftPicks
            };
        }
        */

  };
</script>
<style scoped>
    .draftBody {
          vertical-align: top;  
        }
</style>
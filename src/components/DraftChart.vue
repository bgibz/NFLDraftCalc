<template>
    <div>
        <table>
            <thead>
                <tr>
                    <th v-for="n in numRounds" v-bind:key="n">
                        Round {{n}}
                    </th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td v-for="round in draftRounds" v-bind:key="round.round">
                        <draft-round :round="round" :draftPicks="draftPicks" />
                    </td>
                </tr>
            </tbody>
        </table>
    </div> 
</template>
<script>
  import DraftRound from './DraftRound.vue';
  export default {
  components: { DraftRound },
      props: {
            numRounds: { default: 7, type: Number },
            draftRounds: { required: true, type: Array },
            draftPicks: { required: true, type: Array }
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
       created: function () {
           console.log("Hello World")
        }

  };
</script>
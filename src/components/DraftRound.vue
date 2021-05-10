<template>
    <table>
        <tbody>
            <tr v-for="pick in filterPicks(draftPicks)" v-bind:key="pick.no">
                <td>{{pick.no}}</td>
                <td>{{pick.value}}</td>
            </tr>    
        </tbody>
    </table>
</template>
<script>
  export default {
      props: {
            round: { required: true, type: Object }, // round, first, last pick
            draftPicks: { required: true, type: Array } // matser array of draft picks and values
        },
        data() {
            return {
                draftRound: this.round,
                allDraftPicks: this.draftPicks
            };
        },
        methods: {
            filterPicks: function (picks) {
                return picks.slice(this.draftRound.first - 1, this.draftRound.last);
            }
        }
  };
</script>
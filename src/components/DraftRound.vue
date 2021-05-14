<template>
    <table>
        <tbody>
            <tr v-for="pick in filterPicks(draftPicks)" v-bind:key="pick.no">
                <td class="round-table-td" md-numeric>{{pick.no}}</td>
                <td class="round-table-td" :id="'draft-' + pick.no" :value="pick.value">{{pick.value}}</td>
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
                let length = this.draftRound.last - this.draftRound.first
                let filtered = picks.slice(this.draftRound.first - 1, this.draftRound.last);
                if (filtered.length <= length) {
                    //let count = length - filtered.length;
                    var i;
                    for (i = filtered.length; i <= length; i++) {
                        let newPick = {
                            "no": this.draftRound.first + i,
                            "value": 1
                        }
                        filtered.push(newPick);
                    }
                }
                return filtered;
            }
        }
  };
</script>
<style scoped>
    .round-table-td{
        border-top: none;
        text-align: left;
    }
</style>
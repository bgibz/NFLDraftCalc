<template>
    <md-card class="md-layout-item">
        <md-card-header>
            <div class="md-title">{{this.teamName}}</div>
        </md-card-header>
        <md-card-content>
            <div class="md-layout md-gutter">
                <div class="md-layout-item">
                    <md-field v-for="(pick, index) in tradePicks" :key="index">
                    <label for="Adraft1">Draft Pick To Trade</label>
                    <md-input name="Adraft1" id="Adraft1" v-model="ATeamDraft"/>
                    </md-field>
                    <div class="md-layout">
                        <md-button class="md-icon-button md-raised md-primary" @click="addTradePick">
                            <md-tooltip md-direction="top">Trade another draft pick</md-tooltip>
                            <md-icon>add</md-icon>
                        </md-button>
                    </div>
                </div>
            </div>
        </md-card-content>
    </md-card>
</template>

<script>
export default {
        props: {
            teamName: { required: true, type: String },
        },
    data() {
        return {
                tradePicks: ['','']
            };
    },
    methods: {
        addTradePick: function () {
            this.tradePicks.push({ value: '' });
        }
    }
}
</script>
<style scoped>
    .btn-containter{
        align-content: flex-start;
    }
</style>
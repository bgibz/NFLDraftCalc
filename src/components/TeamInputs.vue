<template>
    <md-card class="md-layout-item">
        <md-card-header>
            <div class="md-title">{{this.teamName}}</div>
        </md-card-header>
        <md-card-content>
            <div class="md-layout md-gutter">
                <div class="md-layout-item">
                    
                    <md-field v-for="(pick, index) in teamTradePicks" :key="index">
                        <label :for="teamName + index">Draft Pick To Trade</label>
                        <md-input :name="teamName + index" :id="teamName + index" :class="teamName+'-draft'" type="number" v-model.number="teamTradePicks[index]" v-on:change="updateTradePicks"/>
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
            tradePicks: {required: true, type: Array}
        },
   data() {
        return {
                teamTradePicks: this.tradePicks
            };
    },
    methods: {
        addTradePick: function () {
            this.tradePicks.push({ value: '' });
        },
        updateTradePicks: function () {
            //console.log(this.tradePicks);
            this.$emit('update-traded-picks', this.tradePicks)
        }
    }
}
</script>
<style scoped>
    .btn-containter{
        align-content: flex-start;
    }
</style>
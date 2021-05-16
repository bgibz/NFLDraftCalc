<template>
    <div class="md-layout">
        <div class="md-layout-item md-size-5"></div>
        <div class="md-layout-item">
            <md-card class="evaluation-card">
                <md-card-content>
                     <button class="md-button md-raised eval-button" @click="evaluateTrade">
                        <md-icon  style="color:white;font:bold;" >play_arrow</md-icon><span> Evaluate Trade</span>
                    </button>
                </md-card-content>
            </md-card>
        </div>
        <div class="md-layout-item md-size-5"></div>
    </div>
</template>

<script>
//import Vue from 'vue';

export default 
    {
        name: 'TradeEvaluation',
        methods: {
            evaluateTrade: function() {
                console.log("Hi!");
            }
        }
    };
</script>
<style scoped>
    .evaluation-card {
        min-height: 100px;
    }
    .eval-button{
        color: white;
        text-align: center;
        background-color: #1AA260;
        min-width: 180px;
    }
</style>
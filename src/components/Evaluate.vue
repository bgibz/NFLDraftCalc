<template>
    <div class="md-layout" v-if="display !== false">
        <div class="md-layout-item md-size-5"></div>
        <div class="md-layout-item">
            <md-card class="evaluation-card">
                <md-card-content>
                    <div class="md-layout">
                        <div class="md-layout-item">
                            <h4>Team A Traded Value:</h4> {{teamAValue}}
                        </div>
                        <div class="md-layout-item">
                            <h4>Team B Traded Value:</h4> {{teamBValue}}
                        </div>
                    </div>
                    <div class="md-layout">
                        <div class="md-layout-item">
                            <div v-if="diff == 0">
                                <h4>This is an even trade</h4>
                            </div>
                            <div v-else-if="diff < 0">
                                <h4>Team A gains </h4> {{diff}} <h4> points through this trade </h4>
                            </div>
                            <div v-else-if="diff > 0">
                                <h4>Team B gains </h4> {{-diff}} <h4> points through this trade </h4>
                            </div>
                        </div>
                    </div>
                </md-card-content>
            </md-card>
        </div>
        <div class="md-layout-item md-size-5"></div>
    </div>
</template>

<script>
export default 
    {
        name: 'TradeEvaluation',
        props: {
            display: {required: true, type: Boolean},
            teamAValue: {required: true, type: Number},
            teamBValue: {required: true, type: Number},
            diff: {required: true, type: Number}
        },
        data: function() {
            return {
                surplus: 0,
                gain: 0,
                equivalent: 0
            }
        }
    };
</script>

<template>
    <div>
        <div>
            <p>Marker Size: {{markerSize}}</p>
            <button @click="setMarkerSize(10)">Reset Marker Size</button>
            <button @click="setMarkerSize(markerSize - 1)">Decrease Marker Size</button>
            <button @click="setMarkerSize(markerSize + 1)">Increase Marker Size</button>
        </div>
        <ag-charts-vue :options="options"></ag-charts-vue>
    </div>
</template>
<script>
    import {AgChartsVue} from "ag-charts-vue";

    export default {
        data() {
            return {
                markerSize: 10,
                options: {}
            }
        },
        components: {
            AgChartsVue,
        },
        methods: {
            setMarkerSize(markerSize) {
                this.markerSize = markerSize;
                this.updateOptions();
            },
            updateOptions() {
                this.options = {
                    data: [{
                        month: 'Jan',
                        revenue: 155000,
                        profit: 33000
                    }, {
                        month: 'Feb',
                        revenue: 123000,
                        profit: 35500
                    }, {
                        month: 'Mar',
                        revenue: 172500,
                        profit: 41000
                    }, {
                        month: 'Apr',
                        revenue: 185000,
                        profit: 50000
                    }],
                    series: [{
                        xKey: 'month',
                        yKey: 'revenue',
                        marker: {
                            size: this.markerSize
                        }
                    }]
                };
            }
        },
        beforeMount() {
            this.updateOptions();
        }
    }
</script>

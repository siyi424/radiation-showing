<template>
  <div id="main" style="width: 100%; height: 600px;"></div>
</template>


<script>
import * as echarts from 'echarts/core';
import { GridComponent } from 'echarts/components';
import { LineChart } from 'echarts/charts';
import { UniversalTransition } from 'echarts/features';
import { CanvasRenderer } from 'echarts/renderers';
import { TooltipComponent } from 'echarts/components';
import { MarkLineComponent} from 'echarts/components';


echarts.use([GridComponent, LineChart, CanvasRenderer, UniversalTransition, TooltipComponent, MarkLineComponent]);


export default {
    props: ['datalist'],
    data() {
        return {
            myuChart: null,
        }
    },
    mounted() {
        let chartDom = document.getElementById('main');
        this.myChart = echarts.init(chartDom);
        let option = {
            xAxis: {
                type: 'category',
                axisPointer: {
                    snap: true,
                },
                data: this.datalist.map(item => item.time),
            },
            yAxis: {
                axisPointer: {
                    snap: true,
                },
            },
            series: [
                {
                    type: "line",
                    data: this.datalist.map(item => item.value),
                    areaStyle: {},
                    markLine: {
                        Symbol: ['none', 'none'],
                        data: [{
                            name: '阈值',
                            yAxis: 200
                        }],
                        lineStyle: {
                            color: '#f00',
                            width: 2,
                            type: 'dashed'
                        },
                    }
                }
            ],
            tooltip: {
                axisPointer: {
                    type: 'cross',
                    label: {
                        backgroundColor: '#6a7985',
                    }
                }
            }
        }

        
        option && this.myChart.setOption(option);


        window.onresize = function() {
            this.myChart.resize();
        };
    },
    watch: {
        datalist: {
            handler() {
                this.myChart.setOption({
                    xAxis: {
                        data: this.datalist.map(item => item.time),
                    },
                    series: [
                {
                    data: this.datalist.map(item => item.value),
                    },
            ],
                })
            }
        }
    }

    
    
}
</script>


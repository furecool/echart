<template>
    <div style="width: 100%; height: 100%;"></div>
</template>

<script>
import * as echarts from 'echarts';
export default {
    name: 'radar-chart',

    mounted() {
        this.initOption();
        this.$nextTick(() => { // 这里的 $nextTick() 方法是为了在下次 DOM 更新循环结束之后执行延迟回调。也就是延迟渲染图表避免一些渲染问题
            this.ready();
        });
    },

    methods: {

        // 初始化图表配置
        initOption() {
            let vm = this;
            vm.option = {
                title: {
                    text: '基础雷达图'
                },
                tooltip: {},
                legend: {
                    data: ['预算分配（Allocated Budget）', '实际开销（Actual Spending）']
                },
                radar: {
                    // shape: 'circle',
                    // alignTicks: false,
                    axisName: {
                        textStyle: {
                            color: '#fff',
                            backgroundColor: '#999',
                            borderRadius: 3,
                            padding: [3, 5]
                        }
                    },
                    indicator: [{ name: '销售（sales）', max: 6500}, { name: '管理（Administration）', max: 16000}, { name: '信息技术（Information Techology）', max: 30000}, { name: '客服（Customer Support）', max: 38000}, { name: '研发（Development）', max: 52000}, { name: '市场（Marketing）', max: 25000}]
                },
                series: [{
                    // alignTicks: false,
                    axisName: '预算 vs 开销（Budget vs spending）',
                    type: 'radar',
                    // areaStyle: {normal: {}},
                    data: [{value: [4300, 10000, 28000, 35000, 50000, 19000], name: '预算分配（Allocated Budget）'}, {value: [5000, 14000, 28000, 31000, 42000, 21000], name: '实际开销（Actual Spending）'}]
                }]
            };
        },

        ready() {
            let vm = this;
            let dom = document.getElementById('radar-chart');

            vm.myChart = echarts.init(dom);
            vm.myChart && vm.myChart.setOption(vm.option);
        },

    },
}
</script>

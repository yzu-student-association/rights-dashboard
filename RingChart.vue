<template>
    <div id="main"></div>
</template>

<script>
import { isProxy, toRaw } from 'vue';

export default {
    name: 'ring-chart',
    props: {
      'data':{
        type: Array
      }
    },
	watch:{
		data: {
			handler(val, oldVal){
				this.updateChart();
			},
			deep: true
		}
	},
    methods: {
      updateChart(){
        var myChart = echarts.init(document.getElementById('main'));
        let rawData = toRaw(this.data);
		console.log(rawData);
        let option = {
          title: {
            text: '專案進度追蹤',
            left: 'center',
            top: 'center',
			textStyle: {fontSize: 24}
          },
          series: [
            {
              type: 'pie',
              color: ['#B5B5B6','#FFF362','#E1893F','#6DA1C8','#73B284','#DD776A'],
              data: rawData,
              radius: ['60%', '70%'],
              label: {formatter: '{b}: {c}',fontSize: 16},
			  colorBy: 'data',
            }
          ],
		  legend: {
			show: true,
			top: 'bottom'
		  }
        };
        myChart.setOption(option);
		
      }
    },
    mounted() {
        this.updateChart();
    }
}

</script>

/*

B5B5B6

FFF362

E1893F

6DA1C8

73B284

DD776A

 */

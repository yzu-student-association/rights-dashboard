<template>
    <div id="main"></div>
</template>

<script>

export default {
    name: 'ring-chart',
    mounted() {
        var myChart = echarts.init(document.getElementById('main'));
        
        let option = {
  title: {
    text: '',
    left: 'center',
    top: 'center'
  },
  series: [
    {
      type: 'pie',
      color: ['lightgray','yellow','skyblue'],
      data: [
        {
          value: 3,
          name: '提案排程中'
        },
        {
          value: 1,
          name: '研議中'
        },
        {
          value: 1,
          name: '辦理中'
        }
      ],
      radius: ['40%', '70%'],
      label: {formatter: '{b}: {c}'}
    }
  ]
};

        myChart.setOption(option);
    }
}

</script>
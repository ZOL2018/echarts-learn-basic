<template style="">
  <div id="chart-carrierStructure" style="height: 100%;width: 100%"></div>
</template>

<script>
  import echarts from 'echarts'
  export default {
    name: 'carrierStructure',
    data() {
      return {
        option: {}
      }
    },
    mounted() {
      this.setOption()
      const chart = echarts.init(document.getElementById('chart-carrierStructure'))
      chart.setOption(this.option)
    },
    methods: {
      setOption() {
        this.option = {
          tooltip: {
            trigger: 'item',
            formatter: '{a} <br/>{b}: {c} ({d}%)'
          },
          // legend: {
          //   orient: 'vertical',
          //   x: 'left',
          //   data: ['区域综合体', '市级综合体', '市级众创空间', '省级众创空间', '国家级众创空间', '市级孵化器', '省级孵化器', '国家级孵化器']
          // },
          series: [
            {
              name: '访问来源',
              type: 'pie',
              selectedMode: 'single',
              radius: [0, '20%'],
              label: {
                normal: {
                  position: 'inner'
                }
              },
              labelLine: {
                normal: {
                  show: false
                }
              },
              data: [
                // { value: 335, name: '综合体', selected: true },
                { value: 679, name: '孵化器' },
                { value: 1548, name: '众创空间' }
              ]
            },
            {
              name: '访问来源',
              type: 'pie',
              radius: ['30%', '45%'],
              label: {
                normal: {
                  formatter: '{b|{b}：}{c}  {per|{d}%}  ',
                  backgroundColor: '#102856',
                  // borderColor: '#aaa',
                  // borderWidth: 1,
                  borderRadius: 2,
                  // shadowBlur:3,
                  // shadowOffsetX: 2,
                  // shadowOffsetY: 2,
                  // shadowColor: '#999',
                  padding: [15, 12],
                  rich: {
                    a: {
                      color: '#999',
                      lineHeight: 22,
                      align: 'center'
                    },
                    // abg: {
                    //     backgroundColor: '#333',
                    //     width: '100%',
                    //     align: 'right',
                    //     height: 22,
                    //     borderRadius: [4, 4, 0, 0]
                    // },
                    // hr: {
                    //   borderColor: '#aaa',
                    //   width: '100%',
                    //   borderWidth: 0.5,
                    //   height: 0
                    // },
                    b: {
                      fontSize: 10,
                      lineHeight: 20
                    },
                    per: {
                      color: '#eee',
                      backgroundColor: '#F39D0E',
                      padding: [2, 4],
                      borderRadius: 4
                    }
                  }
                }
              },
              data: [
                { value: 147, name: '市级' },
                { value: 251, name: '省级' },
                { value: 1048, name: '国家级' },
                { value: 102, name: '区级' },
                { value: 310, name: '国家级' },
                { value: 234, name: '省级' },
                { value: 135, name: '市级' },
                { value: 100, name: '区级' }
              ]
            }
          ]
        }
      }
    }
  }
</script>
<style lang="scss" scoped>
</style>

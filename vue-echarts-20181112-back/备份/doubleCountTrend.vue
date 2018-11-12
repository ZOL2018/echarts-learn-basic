<template>
  <div>
    <el-row>
      <div id="doubleCountTrend" style="width: 540px; height: 365px"></div>
    </el-row>
  </div>
</template>

<script>
  export default {
    name: 'doubleCountTrend',
    data() {
      return {
        option: {
          tooltip: {
            trigger: 'axis',
            axisPointer: {
              type: 'cross',
              crossStyle: {
                color: '#fff'
              }
            }
          },
          grid: {
            top: '60',
            bottom: '100'
          },
          color: ['#00fffc', '#fd9c00'],
          textStyle: {
            color: '#fff'
          },
          legend: {
            textStyle: {
              color: '#fff'
            },
            top: '85%',
            data: ['固定资产投资', '增长率']
          },
          // dataZoom: [
          //   {
          //     type: 'slider', // 表示有滑块的
          //     show: true,
          //     xAxisIndex: [0],
          //     backgroundColor: '#C4D6DA',
          //     fillerColor: '#95A3A6', // 选中范围的填充颜色
          //     top: '90%',
          //     start: 60,
          //     end: 100
          //   },
          //   {
          //     type: 'inside', // 表示内置滚动
          //     show: true,
          //     xAxisIndex: [0],
          //     backgroundColor: '#C4D6DA',
          //     fillerColor: '#95A3A6', // 选中范围的填充颜色
          //     top: '90%',
          //     start: 60,
          //     end: 100
          //   }
          // ],
          xAxis: [
            {
              type: 'category',
              opacity: 0,
              data: ['2013年', '2014年', '2015年', '2016年', '2017年'],
              axisPointer: {
                type: 'shadow'
              },
              axisLine: {
                show: false
              }
            }
          ],
          yAxis: [
            {
              type: 'value',
              // name: '亿元',
              min: 0,
              max: 180,
              // interval: 50,
              axisLabel: {
                formatter: '{value}'
              },
              axisLine: {
                show: false
              },
              splitLine: {
                show: true,
                lineStyle: {
                  color: '#142e50'
                }
              }
            },
            {
              type: 'value',
              // name: '%',
              min: 0,
              max: 30,
              // interval: 5,
              axisLabel: {
                formatter: '{value}'
              },
              axisLine: {
                show: false
              },
              splitLine: {
                show: true,
                lineStyle: {
                  color: '#142e50'
                }
              }
            }
          ],
          series: [
            {
              name: '增长率',
              type: 'line',
              yAxisIndex: 1,
              data: [0, 8, 8, 14, 16],
              itemStyle: {
                normal: {
                  color: '#fd9c00'
                }
              }
            },
            {
              name: '固定资产投资',
              type: 'bar',
              data: [12, 20, 40, 130, 180],
              barWidth: 20,
              itemStyle: {
                normal: {
                  color: new this.$echarts.graphic.LinearGradient(0, 0, 0, 1, [{
                    offset: 0,
                    color: '#00fffe'
                  }, {
                    offset: 1,
                    color: 'rgba(255,255,255,0)'
                  }])
                }
              }
            }
          ]
        }
      }
    },
    mounted() {
      this.draw()
    },
    methods: {
      draw() {
        // 基于准备好的dom，初始化echarts实例
        const chart = this.$echarts.init(document.getElementById('doubleCountTrend'))
        // 绘制图表
        chart.setOption(this.option)
      }
    }
  }
</script>
<style lang="scss" scoped>
</style>

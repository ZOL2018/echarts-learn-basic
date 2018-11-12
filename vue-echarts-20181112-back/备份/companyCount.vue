<template style="">
  <div>
    <el-row>
      <div class="" style="margin:0 auto;text-align: center;width: 524px;height: 275px;" id="companyCount"></div>
    </el-row>
  </div>
</template>
<script>
const datas =
  [[23000, 57, 17096869, 'Australia'],
    [31163, 56.4, 27661240, 'Canada'],
    [75160, 68, 1146077239, 'China'],
    [13670, 74.7, 105822082, 'Cuba'],
    [28599, 75, 4986705, 'Finland'],
    [29476, 77.1, 56943299, 'France'],
    [31476, 75.4, 78958237, 'Germany'],
    [68666, 78.1, 2540830, 'Iceland'],
    [17727, 57.7, 87060176, 'India'],
    [29550, 79.1, 12224925, 'Japan'],
    [2076, 67.9, 20194354, 'North Korea'],
    [42087, 56, 42972254, 'South Korea'],
    [14021, 75.4, 3397534, 'New Zealand'],
    [43296, 56.8, 4240375, 'Norway'],
    [10088, 70.8, 38195258, 'Poland'],
    [19349, 64.6, 147568552, 'Russia'],
    [10670, 77.3, 53994605, 'Turkey'],
    [26424, 87.9, 57110117, 'United Kingdom'],
    [56565, 88, 252847810, 'United States']]
export default {
  name: 'companyCount',
  data() {
    return {
      option: {
        title: {
        },
        grid: {
          top: '20',
          bottom: '20',
          containLabel: true
        },
        xAxis: {
          name: '在孵企业数量',
          nameLocation: 'middle',
          nameGap: '24',
          position: 'center',
          nameRotate: '0',
          nameTextStyle: {
            color: '#eeeeee',
            align: 'center',
            verticalAlign: 'middle'
          },
          axisLine: {
            lineStyle: {
              color: '#2d5f90'
            }
          },
          axisLabel: {
            color: '#eeeeee'
          },
          splitLine: {
            lineStyle: {
              type: 'dashed',
              color: 'rgb(153,153,153,0.5)'
            }
          }
        },
        yAxis: {
          name: '年\n新\n增\n在\n孵\n企\n业\n数\n量',
          nameLocation: 'middle',
          nameGap: '24',
          position: 'center',
          nameRotate: '0',
          nameTextStyle: {
            color: '#eeeeee',
            align: 'center',
            verticalAlign: 'middle'
          },
          axisLine: {
            lineStyle: {
              color: '#2d5f90'
            }
          },
          axisTick: {
            show: false
          },
          axisLabel: {
            color: '#eeeeee'
          },
          splitLine: {
            lineStyle: {
              type: 'dashed',
              color: 'rgb(153,153,153,0.5)'
            }
          },
          scale: true
        },
        series: [{
          name: '',
          data: datas,
          type: 'scatter',
          symbolSize: function(data) {
            return Math.sqrt(data[2]) / 10e2
          },
          label: {
            emphasis: {
              show: true,
              formatter: function(param) {
                return param.data[3]
              },
              position: 'top'
            }
          },
          itemStyle: {
            normal: {
              shadowBlur: 5,
              shadowColor: 'rgba(25, 100, 150, 0.5)',
              shadowOffsetY: 5,
              color: {
                colorStops: [{
                  offset: 0,
                  color: '#90b9cf' // 0% 处的颜色
                }, {
                  offset: 1,
                  color: '#289dc0' // 100% 处的颜色
                }]
              }
            }
          }
        }]
      }
    }
  },
  mounted() {
    this.draw()
  },
  methods: {
    draw() {
      // 基于准备好的dom，初始化echarts实例
      const chart = this.$echarts.init(document.getElementById('companyCount'))
      // 绘制图表
      chart.setOption(this.option)
    },
    names(val) {
      const tmpNam1 = '年新增在孵企业数量'
      const tmpNam2 = '在孵企业数量'
      if (val === 1) { return tmpNam1.split('').join('\n') } else { return tmpNam2.split('').join('\n') }
    }
  }
}
</script>
<style lang="scss" scoped>
</style>

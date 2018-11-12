<template style="">
  <div>
    <el-row>
      <div class="" style="margin:10px auto;text-align: center;width: 460px;height: 420px;" id="countRank"></div>
    </el-row>
  </div>
</template>

<script>
  const datas = [
    ['管城区', '登封市', '经开区', '上街区', '惠济区', '金水区', '中牟县', '巩义市', '荥阳市', '新密区', '中原区', '二七区', '新郑区', '航空港试验区', '高新区', '郑东新区'],
    [360, 400, 450, 500, 520, 560, 600, 680, 750, 800, 880, 900, 920, 1000, 1150, 1200]
  ]
  export default {
    name: 'countRank',
    data() {
      return {
        option: {
          title: {
            text: '航空港区双创载体数量占郑州市比重',
            textStyle: {
              color: '#fefefe',
              fontSize: '10',
              fontWeight: false
            },
            right: '0',
            top: '316'
          },
          tooltip: {
            trigger: 'axis',
            axisPointer: {
              type: 'shadow'
            }
          },
          grid: {
            left: '5',
            top: '0',
            containLabel: true
          },
          xAxis: {
            show: false
          },
          yAxis: {
            nameTextStyle: {
              color: '#FEFEFE',
              fontSize: '14'
            },
            axisLine: {
              lineStyle: {
                color: '#113052'
              }
            },
            axisTick: {
              show: false
            },
            axisLabel: {
              color: '#fff'
            },
            splitLine: {
              lineStyle: {
                type: 'dashed',
                color: 'rgb(153,153,153,0.5)'
              }
            },
            type: 'category',
            data: datas[0]
          },
          series: [
            {
              name: '2011年',
              type: 'bar',
              label: {
                normal: {
                  show: true,
                  position: 'right',
                  fontSize: '10',
                  color: '#fefefe'
                }
              },
              itemStyle: {
                barBorderRadius: [0, 5, 5, 0],
                color: {
                  colorStops: [{
                    offset: 0,
                    color: '#141831' // 0% 处的颜色
                  }, {
                    offset: 1,
                    color: '#078dd1' // 100% 处的颜色
                  }]
                }
              },
              barCategoryGap: '5',
              data: datas[1]
            },
            {
              type: 'pie',
              center: [360, 260],
              radius: [36, 48],
              clockWise: true,
              hoverOffset: 2,
              tooltip: {
                trigger: 'item',
                formatter: function(pram) {
                  return pram.name + ' ' + pram
                    .value + '%'
                }
              },
              itemStyle: {
                normal: {
                  labelLine: {
                    length: 20
                  },
                  color: {
                    colorStops: [{
                      offset: 0,
                      color: '#141831' // 0% 处的颜色
                    }, {
                      offset: 1,
                      color: '#078dd1' // 100% 处的颜色
                    }]
                  }
                }
              },
              data: [
                { value: 75, name: '航空港区双创载体数量占郑州市比重',
                  label: {
                    normal: {
                      show: true,
                      position: 'center',
                      color: '#fb9807',
                      fontSize: '14',
                      formatter: function(parm) {
                        return parm.value + '%'
                      }
                    }
                  }},
                { value: 25, name: '其他区双创载体数量占郑州市比重',
                  itemStyle: {
                    normal: {
                      color: 'transparent'
                    }
                  }}
              ]
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
        const chart = this.$echarts.init(document.getElementById('countRank'))
        // 绘制图表
        chart.setOption(this.option)
      }
    }
  }
</script>
<style lang="scss" scoped>
</style>

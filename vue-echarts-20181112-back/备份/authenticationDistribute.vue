<template style="">
  <div id="chart-authenticationDistribute" style="margin:0 auto;text-align: center;width: 524px;height: 275px;"></div>
</template>

<script>
  import echarts from 'echarts'
  export default {
    name: 'authenticationDistribute',
    data() {
      return {
        option: {}
      }
    },
    mounted() {
      this.setOption()
      const chart = echarts.init(document.getElementById('chart-authenticationDistribute'))
      chart.setOption(this.option)
    },
    methods: {
      setOption() {
        this.option = {
          title: {
          },
          tooltip: {
            trigger: 'item',
            formatter: function(pram) {
              return pram.name + '，' + pram.value
            }
          },
          series: [
            {
              name: '创新平台',
              type: 'pie',
              radius: ['48%', '68%'],
              data: [
                { value: 21,
                  name: '实验室',
                  itemStyle: {
                    color: '#00fefe'
                  }
                },
                { value: 12,
                  name: '研发中心',
                  itemStyle: {
                    color: '#00ed8d'
                  }
                },
                { value: 16,
                  name: '技术中心',
                  itemStyle: {
                    color: '#01a5fc'
                  }
                },
                {
                  value: 0,
                  name: '创新平台',
                  label: {
                    normal: {
                      show: true,
                      position: 'center',
                      color: '#eeeeee',
                      fontSize: '16',
                      formatter: function(parm) {
                        return parm.name
                      }
                    }
                  }
                }
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

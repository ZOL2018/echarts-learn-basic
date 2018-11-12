<template style="">
  <div id="map-zhouzheng" style="margin:10px auto;text-align: center;width: 560px;height: 420px;">

  </div>
</template>

<script>
  import echarts from 'echarts'
  import 'echarts-gl'
  import zhengzhou from '../../../../static/js/zhengzhou'
  export default {
    name: 'mapCount',
    data() {
      return {
        option: {},
        geoCoordMap: {
          '郑州市': [113.62, 34.75],
          '中原区': [113.60, 34.75],
          '二七区': [113.65, 34.73],
          '管城回族区': [113.67, 34.75],
          '金水区': [113.65, 34.78],
          '上街区': [113.28, 34.82],
          '惠济区': [113.60, 34.87],
          '中牟县': [113.97, 34.72],
          '巩义市': [112.98, 34.77],
          '荥阳市': [113.40, 34.78],
          '新密市': [113.38, 34.53],
          '新郑市': [113.73, 34.40],
          '登封市': [113.03, 34.47]
        },
        alirl: [null]
      }
    },
    mounted() {
      echarts.registerMap('zhengzhou', zhengzhou)
      this.init_option()
      const chart = echarts.init(document.getElementById('map-zhouzheng'))
      chart.setOption(this.option)
    },
    methods: {
      convertData(data) {
        var res = []
        for (var i = 0; i < data.length; i++) {
          var geoCoord = this.geoCoordMap[data[i].name]
          if (geoCoord) {
            res.push({
              name: data[i].name,
              value: geoCoord.concat(data[i].value)
            })
          }
        }
        return res
      },
      init_option() {
        this.option = {
          title: {
          },
          tooltip: {
            show: false
          },
          geo3D: {
            map: 'zhengzhou',
            itemStyle: {
              color: '#0a87d9',
              opacity: 1,
              borderWidth: 1,
              borderColor: '#333333'
            },
            label: {
              show: true,
              distance: '500',
              textStyle: {
                color: '#fff',
                fontSize: 6,
                opacity: 1,
                backgroundColor: 'rgba(13,23,82,0.6)',
                borderWidth: '1',
                borderColor: '#01b5f0',
                padding: [5, 10, 5, 10]
              }
            },
            emphasis: {
              itemStyle: {
                color: '#e69091'
              }
            },
            light: {
              main: {
                color: '#fff',
                intensity: 1.2,
                shadow: false,
                alpha: 55,
                beta: 10
              },
              ambient: {
                intensity: 0.5
              }
            }
          },
          series: [
            // 柱状图
            {
              name: 'bar3D',
              type: 'bar3D',
              coordinateSystem: 'geo3D',
              barSize: 3, // 柱子粗细
              shading: 'lambert',
              opacity: 1,
              bevelSize: 0.3,
              bevelSmoothness: 100,
              label: {
                distance: '2',
                formatter: '{b}{c}',
                textStyle: {
                  color: '#333333',
                  backgroundColor: '#fff'
                }
              },
              itemStyle: {
                color: '#5ef0d8'
              },
              emphasis: {
                itemStyle: {
                  color: '#e69091'
                }
              },
              data: this.convertData([{
                name: '郑州市',
                value: 500
              }, {
                name: '中原区',
                value: 400
              }, {
                name: '二七区',
                value: 420
              }, {
                name: '管城回族区',
                value: 5
              }, {
                name: '金水区',
                value: 60
              }, {
                name: '上街区',
                value: 32
              }, {
                name: '惠济区',
                value: 450
              }, {
                name: '中牟县',
                value: 300
              }, {
                name: '巩义市',
                value: 231
              }, {
                name: '荥阳市',
                value: 331
              }, {
                name: '新密市',
                value: 111
              }, {
                name: '新郑市',
                value: 279
              }, {
                name: '登封市',
                value: 180
              }
              ])
            }
          ]
        }
      }
    }
  }
</script>
<style lang="scss" scoped>
</style>

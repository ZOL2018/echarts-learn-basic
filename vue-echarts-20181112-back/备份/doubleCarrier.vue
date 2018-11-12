<template>
  <div class="main">
    <el-row :gutter="20">

      <el-col :span="24">
        <el-row :gutter="20">
          <el-col :span="8">
            <div class="middle_chart">
              <div class="ms-box">
                <span>郑州航空港区双创载体数量趋势</span>
                <doubleCountTrend></doubleCountTrend>
              </div>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="middle_chart">
              <div class="ms-box">
                <span></span>
                <mapCount></mapCount>
              </div>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="middle_chart">
              <div class="ms-box">
                <span>郑州市双创载体数量排行榜</span>
                <countRank></countRank>
              </div>
            </div>
          </el-col>
        </el-row>
      </el-col>

      <el-col :span="24">
        <el-row :gutter="20">
          <el-col :span="8">
            <div class="middle_chart">
              <div class="ms-box">
                <span>双创载体结构</span>
                <carrierStructure></carrierStructure>
              </div>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="middle_chart">
              <div class="ms-box">
                <span>在孵企业数量</span>
                <companyCount></companyCount>
              </div>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="middle_chart">
              <div class="ms-box">
                <span>认证分布</span>
                <authenticationDistribute></authenticationDistribute>
              </div>
            </div>
          </el-col>
        </el-row>
      </el-col>

    </el-row>
  </div>
</template>

<script>
  import authenticationDistribute from './authenticationDistribute'
  import carrierStructure from './carrierStructure'
  import companyCount from './companyCount'
  import countRank from './countRank'
  import doubleCountTrend from './doubleCountTrend'
  import mapCount from './mapCount'
  export default {
    components: { authenticationDistribute, carrierStructure, companyCount, countRank, doubleCountTrend, mapCount },
    name: 'doubleCarrier'
  }
</script>
<style lang="scss" scoped>
  $middle_chart: 25rem;
  .main{
    margin: 0 1rem 0 1rem;
  }
  .ms-box {
    height: 100%;
    border: 1px solid rgb(62, 146, 196);
    border-radius: 3px 3px 0 0;
  }

  .middle_chart {
    height: $middle_chart;
    margin-bottom: 1rem;
  }

  .middle_chart_x2 {
    height: $middle_chart*2+1;
    margin-bottom: 1rem;
  }
  .tile_chart{
    display: flex;
  }
</style>

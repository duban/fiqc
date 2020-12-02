<template>
  <div class="dashboard-editor-container">
    <el-row :gutter="18" class="panel-group">
      <el-col :xs="18" :sm="18" :lg="24" class="filter">
        <el-form :inline="true" :model="filter" class="filter-form">
          <div class="filter-form-left">
            <el-form-item label="Date Range">
              <el-date-picker
                v-model="filter.dates"
                type="datetimerange"
                range-separator="To"
                start-placeholder="Start Date"
                format="yyyy-MM-dd"
                end-placeholder="End Date"
              />
            </el-form-item>
            <el-form-item label="Agent">
              <el-select v-model="filter.agent" placeholder="Please Select Agent">
                <el-option label="Agent1" value="ag1" />
                <el-option label="Agent2" value="ag2" />
              </el-select>
            </el-form-item>
            <el-form-item>
              <el-button type="primary" @click="onSubmit">Apply</el-button>
            </el-form-item>
          </div>
        </el-form>
      </el-col>
      <el-col :xs="18" :sm="18" :lg="8">
        <div class="chart-wrapper">
          <bar-chart />
        </div>
      </el-col>
      <el-col :xs="18" :sm="18" :lg="16">
        <div class="chart-wrapper">
          <bar-series style="width: 100%;height: 250px" />
        </div>
      </el-col>
      <el-col :xs="24" :sm="24" :lg="8">
        <div class="chart-wrapper">
          <pie-chart />
        </div>
      </el-col>
      <el-col :xs="24" :sm="24" :lg="8">
        <div class="chart-wrapper">
          <word-cloud />
        </div>
      </el-col>
      <el-col :xs="24" :sm="24" :lg="12">
        <div class="chart-wrapper">
          <heat-map style="width: 100%;height: 250px" chart-title="Speed of Calls" />
        </div>
      </el-col>
      <el-col :xs="24" :sm="24" :lg="12">
        <div class="chart-wrapper">
          <heat-map style="width: 100%;height: 250px" chart-title="Amplitude of Calls" />
        </div>
      </el-col>
      <el-col :xs="24" :sm="24" :lg="12">
        <div class="chart-wrapper">
          <heat-map style="width: 100%;height: 250px" chart-title="Change Speed of Calls" />
        </div>
      </el-col>
      <el-col :xs="20" :sm="20" :lg="12">
        <div class="chart-wrapper">
          <heat-map style="width: 100%;height: 250px" chart-title="Change Amplitude of Calls" />
        </div>
      </el-col>
    </el-row>
  </div>

</template>

<script>
// import GithubCorner from '@/components/GithubCorner'
// import PanelGroup from './components/PanelGroup'
// import LineChart from './components/MixChart'
// import RaddarChart from './components/RaddarChart'
// import PieChart from './components/PieChart'
import WordCloud from './components/WordCloud'
import HeatMap from './components/HeatMap'
import BarChart from './components/BarChart'
// import LineChart from '../charts/line'
import BarSeries from './components/BarSeriesChart'
import PieChart from '../dashboard/admin/components/PieChart'
// import TransactionTable from './components/TransactionTable'
// import TodoList from './components/TodoList'
// import BoxCard from './components/BoxCard'

const lineChartData = {
  newVisitis: {
    expectedData: [100, 120, 161, 134, 105, 160, 165],
    actualData: [120, 82, 91, 154, 162, 140, 145]
  },
  messages: {
    expectedData: [200, 192, 120, 144, 160, 130, 140],
    actualData: [180, 160, 151, 106, 145, 150, 130]
  },
  purchases: {
    expectedData: [80, 100, 121, 104, 105, 90, 100],
    actualData: [120, 90, 100, 138, 142, 130, 130]
  },
  shoppings: {
    expectedData: [130, 140, 141, 142, 145, 150, 160],
    actualData: [120, 82, 91, 154, 162, 140, 130]
  }
}

export default {
  name: 'DashboardAdmin',
  components: {
    PieChart,
    // GithubCorner,
    BarChart,
    BarSeries,
    HeatMap,
    WordCloud
    // ,
    // RaddarChart,
    // PieChart,
    // TransactionTable,
    // TodoList,
    // BoxCard
  },
  data() {
    return {
      filter: {
        dates: ['2020-10-11', '2020-10-22'],
        agent: 'ag1'
      },
      lineChartData: lineChartData.newVisitis
    }
  },
  methods: {
    handleSetLineChartData(type) {
      this.lineChartData = lineChartData[type]
    }
  }
}
</script>

<style lang="scss" scoped>
.dashboard-editor-container {
  padding: 15px;
  background-color: rgb(240, 242, 245);
  position: relative;

  .github-corner {
    position: absolute;
    top: 0px;
    border: 0;
    right: 0;
  }

  .chart-wrapper {
    background: #fff;
    padding: 16px 16px 0;
    margin-bottom: 16px;
  }
}

@media (max-width:1024px) {
  .chart-wrapper {
    padding: 10px;
  }
}
</style>

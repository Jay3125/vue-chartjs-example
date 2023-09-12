<template>
    <div class="container">
      <div class="row justify-content-center align-items-center g-2">
      
        <div class="col-md-4 mb-4">
          <canvas id="planet-chart" :options="planetChartData"></canvas> 
        </div>
        <!-- <div class="col-md-4 mb-4">
          <Line id="planet-chart" :data="planetChartData.data" :options="planetChartData.options"></Line> 
        </div> -->
        <div class="col-md-4 mb-4">
          <Bar :data="planetChartData.data" :options="planetChartData.options" />
        </div>
        <div class="col-md-4 mb-4">
          <Pie :data="planetChartData.data" :options="planetChartData.options" />
        </div>
        <div class="col-md-4 mb-4">
          <PolarArea :data="planetChartData.data" :options="planetChartData.options" />
        </div>
        <div class="col-md-4 mb-4">
          <Radar :data="planetChartData.data" :options="planetChartData.options" />
        </div>
        <div class="col-md-4 mb-4">
          <Scatter :data="planetChartData.data" :options="planetChartData.options" />
        </div>
        <div class="col-md-4 mb-4">
          <Bubble :data="planetChartData.data" :options="planetChartData.options" />
        </div>
        <div class="col-md-4 mb-4">
          <Doughnut :data="planetChartData.data" :options="planetChartData.options" />
        </div>
      </div>
      <div class="row">
      </div>
    </div>
  </template>
  
  <script lang="js">
  // import Chart from 'chart.js/auto';
  import  Chart, {
  Chart as ChartJS,
  Title,
  Tooltip,
  Legend,
  BarElement,
  CategoryScale,
  LinearScale,
} from 'chart.js/auto'
  import { Bar,Pie,PolarArea,Radar,Scatter,Bubble, Doughnut } from 'vue-chartjs'

  ChartJS.register(CategoryScale, LinearScale, BarElement, Title, Tooltip, Legend)

  import planetChartData from '../planetData';
  export default {
    name: 'PlanetChart',
    props:{option:{type:Object}},
    components: {
    Bar,
    Pie,
    // Line,
    PolarArea,
    Radar,Scatter,Bubble,Doughnut
},
    data() {
    return {
      planetChartData: planetChartData,
      data: {
        labels: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'],
        datasets: [{ data:[49.9, 71.5, 106.4, 129.2, 144.0, 176.0, 135.6, 148.5, 216.4, 194.1, 95.6, 54.4] }]
      },
      options: {
        responsive: true,
        legend: {
          display: false
      },
      },
   
    }
  },
  mounted() {
    const ctx = document.getElementById('planet-chart');
    new Chart(ctx, this.planetChartData);
  }
  }
  </script>
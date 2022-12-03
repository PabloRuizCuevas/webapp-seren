<script lang="ts">
  import {Chart } from 'svelte-chartjs';

  import {
    Chart as ChartJS,
    Tooltip,
    Legend,
    BarElement,
    PointElement,
    LineElement,
    CategoryScale,
    LinearScale,
    LineController,
    BarController,
  } from 'chart.js';

  ChartJS.register(
    LinearScale,
    CategoryScale,
    BarElement,
    PointElement,
    LineElement,
    Legend,
    Tooltip,
    LineController,
    BarController,
  );

  export let animation: boolean;
  export let salary: number;
  export let pension = 8;
  export let sick = 2;
  export let accident = 2;

  let chart: Chart;

  const labels = ['Salary', 'Pension', 'Insurance', 'Worst Case'];


  export const data = {
    labels,
    datasets: [
      {
        type: 'bar',
        label: 'Dataset 2',
        backgroundColor: ['rgb(75, 192, 192)','rgb(75, 122, 142)','rgb(75, 112, 192)','rgb(175, 92, 92)'],
        data: [salary, pension, sick, accident],
        borderColor: 'white',
        borderWidth: 2,
      }
    ],
  };

  export const options = {
      scales: {
        y: {
          beginAtZero: true,
        },
      },
      animation: {
        duration: 1000,
        animation: animation
      },
      plugins: {
        legend: {
          display: false
        }
      },
      maintainAspectRatio: false
  };

  $: {if (chart) {
      chart.options.animation.animation = animation
      chart.data.datasets[0].data = [salary, pension, sick, accident];
      
    }
  }

</script>

<div class="chart">
  <Chart bind:chart 
  type="bar"
  data={data}
  options={options} />
</div>

<style>
  .chart{
    border-radius: 10px;
    box-shadow:0 0 15px 4px rgba(0,0,0,0.06);
    margin: 10px;
    padding: 10px;
    height: 280px;
  }

</style>
<script lang="ts">
  import { Doughnut } from 'svelte-chartjs';
  import { data } from './data.js';

  import {
    Chart as ChartJS,
    Title,
    Tooltip,
    Legend,
    ArcElement,
    CategoryScale,
  } from 'chart.js';

  ChartJS.register(Title, Tooltip, Legend, ArcElement, CategoryScale);

  export let animation: boolean;
  export let gross = 3e4
  export let tax = 0.45
  export let pension = 0.1
  export let eftax

  const options = {
    animation: {
      duration: 1000,
      animation: animation
    },
    plugins: {
      legend: {
        display: true,
        position: 'right'
      },            
      title: {
              display: true,
              text: 'Gross Income:  ' + gross + '  krowns'
          }
      
    },
    /* responsive: true,*/
    maintainAspectRatio: false
  };

  let chart: Doughnut;


  $: {if (chart) {
      let taxed = gross*(1-pension)*tax
      let remaining = gross - taxed- gross*pension

      chart.options.animation.animation = animation
      chart.data.datasets[0].data = [ remaining, taxed, gross*pension];

      eftax = taxed/gross
    }
  }


</script>

<div class="chart">
  <Doughnut bind:chart data={data} options={options} />

</div>

<style>
  .chart{
    border-radius: 10px;
    box-shadow:0 0 15px 4px rgba(0,0,0,0.06);
    margin: 10px;
    padding: 10px;
    width: 600px;
  }

</style>
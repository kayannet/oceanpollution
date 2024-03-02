<!-- BarChart.svelte -->

<script>
  import { scaleBand, scaleLinear } from "d3-scale";
  import { onMount } from 'svelte';
  import { csv } from 'd3-fetch';

  let data = []; // Initialize data with an empty array

  // Load data from CSV file
  onMount(async () => {
    const response = await fetch("/static/csv data/mismanaged-plastic-waste-per-capita.csv"); // Adjust the path to your CSV file
    const csvData = await response.text();
    data = d3.csvParse(csvData);
    createChart(); // Call createChart function after loading the data
  });

  let width = 800;
  let height = 600;

  const margin = { top: 20, right: 20, bottom: 20, left: 180 };
  const innerHeight = height - margin.top - margin.bottom;
  const innerWidth = width - margin.left - margin.right;

  $: xDomain = data.map((d) => d.Entity);
  $: yDomain = data.map((d) => +d['Mismanaged plastic waste per capita (kg per year)']);

  $: xScale = scaleLinear().domain([0, Math.max(...yDomain)]).range([0, innerWidth]);
  $: yScale = scaleBand().domain(xDomain).range([0, innerHeight]).padding(0.1);

  function createChart() {
    // The rest of your chart creation code
    // Make sure to use reactive variables (prefixed with $:) to update the chart when data changes
  }
</script>

<svg {width} {height}>
  <g transform={`translate(${margin.left},${margin.top})`}>
    {#each data as d}
      <!-- Render bars and labels here -->
    {/each}
  </g>
</svg>

<script>
    import { scaleBand, scaleLinear } from "d3-scale";
  
    export let data;
  
    let width = 800;
    let height = 600;
  
    const margin = { top: 20, right: 20, bottom: 20, left: 180 };
    const innerHeight = height - margin.top - margin.bottom;
    const innerWidth = width - margin.left - margin.right;
  
    $: xDomain = data.map((d) => d.Entity);
    $: yDomain = data.map((d) => +d.Mismanaged_plastic_waste_per_capita_kg_per_year);
  
    $: yScale = scaleBand().domain(xDomain).range([0, innerHeight]).padding(0.1);
    $: xScale = scaleLinear()
      .domain([0, Math.max.apply(null, yDomain)])
      .range([0, innerWidth]);
  </script>
  
  <svg {width} {height}>
    <g transform={`translate(${margin.left},${margin.top})`}>
      {#each xScale.ticks() as tickValue}
        <g transform={`translate(${xScale(tickValue)},0)`}>
          <line y2={innerHeight} stroke="black" />
          <text text-anchor="middle" dy=".7em" y={innerHeight + 3}>
            {tickValue}
          </text>
        </g>
      {/each}
      {#each data as d}
        <text
          text-anchor="end"
          x="-3"
          dy=".3em"
          y={yScale(d.Entity) + yScale.bandwidth() / 2}
        >
          {d.Entity}
        </text>
        <rect
          x="0"
          y={yScale(d.Entity)}
          width={xScale(d.Mismanaged_plastic_waste_per_capita_kg_per_year)}
          height={yScale.bandwidth()}
        />
      {/each}
    </g>
  </svg>
  
<script>
  import { scaleBand, scaleLinear } from "d3-scale";
  import { onMount } from "svelte";

  export let data;

  let width = 800;
  let height = 600;

  const margin = { top: 20, right: 20, bottom: 50, left: 80 };
  const innerHeight = height - margin.top - margin.bottom;
  const innerWidth = width - margin.left - margin.right;

  let xDomain, yDomain, xScale, yScale;

  onMount(() => {
    xDomain = data.map((d) => d.Entity);
    yDomain = data.map((d) => +d.Value);

    xScale = scaleBand().domain(xDomain).range([0, innerWidth]).padding(0.1);
    yScale = scaleLinear()
      .domain([0, Math.max(...yDomain)])
      .range([innerHeight, 0]);
  });

  function handleMouseOver(event, d) {
    const rect = event.target;
    const value = d.Value;

    rect.setAttribute("fill", "orange");

    const tooltip = document.getElementById("tooltip");
    tooltip.style.display = "block";
    tooltip.style.left = event.clientX + "px";
    tooltip.style.top = event.clientY + "px";
    tooltip.textContent = `Value: ${value}`;
  }

  function handleMouseOut(event) {
    const rect = event.target;
    rect.setAttribute("fill", "steelblue");

    const tooltip = document.getElementById("tooltip");
    tooltip.style.display = "none";
  }
</script>

<svg {width} {height}>
  <g transform={`translate(${margin.left},${margin.top})`}>
    {#each data as d}
      <rect
        x={xScale(d.Entity)}
        y={yScale(d.Value)}
        width={xScale.bandwidth()}
        height={innerHeight - yScale(d.Value)}
        fill="steelblue"
        on:mouseover={(event) => handleMouseOver(event, d)}
        on:mouseout={handleMouseOut}
      />
    {/each}
  </g>
</svg>

<div id="tooltip" style="position: absolute; display: none; background-color: white; padding: 5px; border: 1px solid black;"></div>

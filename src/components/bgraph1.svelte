<script>
  import { scaleBand, scaleLinear } from "d3-scale";
  import { createEventDispatcher } from "svelte";

  export let data;

  const dispatch = createEventDispatcher();

  let width = 1000;
  let height = 3000;

  const margin = { top: 20, right: 20, bottom: 20, left: 220 }; // Increased bottom margin for better tooltip display
  const innerHeight = height - margin.top - margin.bottom;
  const innerWidth = width - margin.left - margin.right;

  let xDomain = data.map((d) => d.Entity);
  let yDomain = data.map((d) => +d.Value);

  let yScale = scaleBand().domain(xDomain).range([0, innerHeight]).padding(0.1);
  let xScale = scaleLinear()
    .domain([0, Math.max(...yDomain)])
    .range([0, innerWidth]);

  function handleMouseOver(d) {
    const rect = this.getBoundingClientRect();
    const x = rect.left + window.scrollX;
    const y = rect.top + window.scrollY;

    dispatch("tooltip", {
      x: x + rect.width / 2,
      y: y - 10,
      content: d.Value
    });
  }

  function handleMouseOut() {
    dispatch("tooltip", null);
  }
</script>

<!-- <div class="chart" bind:clientWidth={width} bind:clientHeight={height}> -->

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
          width={xScale(d.Value)}
          height={yScale.bandwidth()}
          on:mouseover={() => handleMouseOver(d)}
          on:mouseout={handleMouseOut}
        />
      {/each}
    </g>

   
  </svg>
<!-- </div> -->

<style>
  /* .svg {
		position: relative;
		width: 1000px;
		height: 10000px;
	} */
</style>

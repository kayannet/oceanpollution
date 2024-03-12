<script>
	import { scaleLinear } from 'd3-scale';

	const points = [
		{ entity: 'Asia', share: 80.99 },
		{ entity: 'Africa', share: 7.98 },
		{ entity: 'South America', share: 5.51 },
		{ entity: 'North America', share: 4.49 },
		{ entity: 'Europe', share: 0.59 },
		{ entity: 'Australia', share: 0.0032 }
	];

//     0,Asia,80.99356991
// 1,Africa,7.98931654
// 2,South America,5.513253248
// 3,North America,4.499120942
// 4,Europe,0.595431351
// 5,Australia,0.003267113


	const xTicks = ['Asia', 'Africa', 'South America', 'North America', 'Europe', 'Australia'];
	const yTicks = [0, 10, 20, 30, 40, 50, 60, 70, 80];
	const padding = { top: 20, right: 15, bottom: 20, left: 25 };

	let width = 600;
	let height = 300;

	function formatMobile(tick) {
		return "'" + tick.toString().slice(-2);
	}

	$: xScale = scaleLinear()
		.domain([0, xTicks.length])
		.range([padding.left, width - padding.right]);

	$: yScale = scaleLinear()
		.domain([0, Math.max.apply(null, yTicks)])
		.range([height - padding.bottom, padding.top]);

	$: innerWidth = width - (padding.left + padding.right);
	$: barWidth = innerWidth / xTicks.length;
</script>

<h2>Waste Emitted to Ocean by Continent</h2>

<div class="chart" bind:clientWidth={width} bind:clientHeight={height}>
	<svg>
		<!-- y axis -->
		<g class="axis_y-axis">
			{#each yTicks as tick}
				<g class="tick tick-{tick}" transform="translate(0, {yScale(tick)})">
					<line x2="100%" />
					<text y="-4">{tick}</text>
				</g>
			{/each}
		</g>

		<!-- x axis -->
		<g class="axis x-axis">
			{#each points as point, i}
				<g class="tick" transform="translate({xScale(i)},{height})">
					<text x={barWidth / 2} y="-6">{width > 380 ? point.entity : formatMobile(point.entity)}</text>
				</g>
			{/each}
		</g>

		<g class="bars">
			{#each points as point, i}
				<rect
					x={xScale(i) + 2}
					y={yScale(point.share)}
					width={barWidth - 4}
					height={yScale(0) - yScale(point.share)}
				/>

                <text
                    x={xScale(i) + barWidth / 2}
                    y={yScale(point.share) - 5} 
                    text-anchor="middle"
                    fill="white"
                    font-size = 15
                    font-family= Futura
                >
                    {point.share}%
                    
                </text>
			{/each}
		</g>
	</svg>
</div>

<style>
	h2 {
		text-align: center;
        margin: 13;
        font-family: Futura;

	}

	.chart {
		height: 100%;
		max-width: 100%;
		margin: auto;
	}

	svg {
		position: relative;
		width: 100%;
		height: 300px;
        margin: auto;
	}

	.tick {
		font-family: Futura;
		font-size: 0.725em;
		font-weight: 200;

	}

	.tick line {
		stroke: #e2e2e2;
		stroke-dasharray: 2;

	}

	.tick text {
		fill: white;
		text-anchor: start;

	}

	.tick.tick-0 line {
		stroke-dasharray: 0;

	}

	.x-axis .tick text {
		text-anchor: middle;

	}

	.bars rect {
		fill: #a11;
		stroke: none;
		opacity: 0.65;

	}

</style>



<!-- <script>
	import * as d3 from 'd3';
	import {onMount} from 'svelte';
	
	let data = [];
	onMount(async function() {
		data = await d3.csv('src/components/top_continents_plastics_emitted_to_ocean.csv', (d) => ({
			...d,
			entity: +d.Entity,
			share: +d.Share_of_global_plastics_emitted_to_ocean,
		}));
		console.log(data);
	});
	
	$: xScale = d3.scaleLinear()
		.domain([0, d3.max(data, (d) => d.Share_of_global_plastics_emitted_to_ocean)])
		.range([0, 400]);
	
	$: colorScale = d3.scaleOrdinal()
		.domain(data.map(d => d.Entity))
		.range(d3.schemeTableau10)
</script>

{#each data as d}
	<div class="bar" style="width: {xScale(d.Share_of_global_plastics_emitted_to_ocean)}px; background: {colorScale(d.Entity)}">
		{d.Entity}: {d.Share_of_global_plastics_emitted_to_ocean}
	</div>
{/each}

<style>
	.bar {
		background: steelblue;
		padding: 3px;
		margin: 1px;
		text-align: right;
		color: black;
		width: 0px;
        font-family: Futura;
	}
</style> -->
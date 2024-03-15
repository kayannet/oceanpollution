<script>
	import { onMount } from 'svelte';
	import * as d3 from 'd3';

	let data = [
		{ label: 'AFR', value: 10.46592827 },
		{ label: 'ALB', value: 24.23915307 },
		{ label: 'DZA', value: 17.75899473 },
		{ label: 'AGO', value: 7.445278869 },
		{ label: 'ATG', value: 6.463917526 },
		{ label: 'ARG', value: 10.40191152 },
		{ label: 'ASIA', value: 8.667235444 },
		{ label: 'AUS', value: 0.20894338 },
		{ label: 'BHS', value: 5.686375321 },
		{ label: 'BHR', value: 0.635588056 },
		{ label: 'BGD', value: 6.268108387 },
		{ label: 'BRB', value: 3.038327526 },
		{ label: 'BEL', value: 0.19793743 },
		{ label: 'BLZ', value: 15.43846154 },
		{ label: 'BEN', value: 11.29861876 },
		{ label: 'BIH', value: 16.82853681 },
		{ label: 'BRA', value: 15.62046908 },
		{ label: 'BRN', value: 1.598152425 },
		{ label: 'BGR', value: 0.445285714 },
		{ label: 'BFA', value: 15.61429064 },
		{ label: 'KHM', value: 15.01152423 },
		{ label: 'CMR', value: 22.36814036 },
		{ label: 'CAN', value: 0.630483013 },
		{ label: 'CPV', value: 6.487272727 },
		{ label: 'CHL', value: 1.623417054 },
		{ label: 'CHN', value: 8.559308412 },
		{ label: 'COL', value: 1.697570472 },
		{ label: 'COM', value: 69.51586369 },
		{ label: 'COG', value: 12.13361829 },
		{ label: 'CRI', value: 1.139263074 },
		{ label: 'CIV', value: 11.33934751 },
		{ label: 'HRV', value: 4.247941889 },
		{ label: 'CYP', value: 0.698081735 },
		{ label: 'COD', value: 15.78193592 },
		{ label: 'DNK', value: 0.067567568 },
		{ label: 'DJI', value: 10.56365503 },
		{ label: 'DMA', value: 15.02777778 },
		{ label: 'DOM', value: 18.06667287 },
		{ label: 'TLS', value: 13.33642691 },
		{ label: 'ECU', value: 6.262058248 },
		{ label: 'EGY', value: 14.29961748 },
		{ label: 'SLV', value: 3.361171367 },
		{ label: 'GNQ', value: 6.934365782 },
		{ label: 'ERI', value: 24.0457535 },
		{ label: 'EST', value: 0.452488688 },
		{ label: 'EUR', value: 1.580226046 },
		{ label: 'FJI', value: 4.334831461 },
		{ label: 'FIN', value: 0.473788865 },
		{ label: 'FRA', value: 0.426531552 },
		{ label: 'GUF', value: 0.432989691 },
		{ label: 'GAB', value: 2.757017948 },
		{ label: 'GMB', value: 14.9467632 },
		{ label: 'GEO', value: 0.076807606 },
		{ label: 'DEU', value: 0.606774669 },
		{ label: 'GHA', value: 17.09520679 },
		{ label: 'GRC', value: 0.430249212 },
		{ label: 'GRD', value: 12.11607143 },
		{ label: 'GLP', value: 0.405 },
		{ label: 'GTM', value: 17.68972186 },
		{ label: 'GIN', value: 11.58852087 },
		{ label: 'GNB', value: 10.65330557 },
		{ label: 'GUY', value: 35.20434227 },
		{ label: 'HTI', value: 21.12829619 },
		{ label: 'HND', value: 14.97999179 },
		{ label: 'HKG', value: 0.777434104 },
		{ label: 'ISL', value: 0.445427729 },
		{ label: 'IND', value: 9.509608 },
		{ label: 'IDN', value: 3.045657286 },
		{ label: 'IRN', value: 5.981679813 },
		{ label: 'IRQ', value: 12.51007377 },
		{ label: 'IRL', value: 0.547931176 },
		{ label: 'ISR', value: 0.711351098 },
		{ label: 'ITA', value: 0.640842279 },
		{ label: 'JAM', value: 16.84972863 },
		{ label: 'JPN', value: 0.281286458 },
		{ label: 'JOR', value: 12.31686795 },
		{ label: 'KAZ', value: 2.92393941 },
		{ label: 'KEN', value: 5.514455815 },
		{ label: 'KIR', value: 0.627118644 },
		{ label: 'KWT', value: 0.627525553 },
		{ label: 'LVA', value: 0.500786576 },
		{ label: 'LBN', value: 6.800175029 },
		{ label: 'LSO', value: 14.30164706 },
		{ label: 'LBR', value: 8.087907636 },
		{ label: 'LBY', value: 27.81983178 },
		{ label: 'LTU', value: 0.375724638 },
		{ label: 'MDG', value: 0.936260151 },
		{ label: 'MYS', value: 25.491518 },
		{ label: 'MDV', value: 0.11299435 },
		{ label: 'MLT', value: 0.588636364 },
		{ label: 'MHL', value: 0.271186441 },
		{ label: 'MTQ', value: 0.369680851 },
		{ label: 'MRT', value: 4.594785683 },
		{ label: 'MUS', value: 0.235433071 },
		{ label: 'MEX', value: 3.375352731 },
		{ label: 'MCO', value: 0.128205128 },
		{ label: 'MNE', value: 0.025477707 },
		{ label: 'MAR', value: 8.101776705 },
		{ label: 'MOZ', value: 14.30652704 },
		{ label: 'MMR', value: 8.038338422 },
		{ label: 'NAM', value: 8.373547094 },
		{ label: 'NLD', value: 0.890975025 },
		{ label: 'NZL', value: 0.358352498 },
		{ label: 'NIC', value: 16.93583868 },
		{ label: 'NGA', value: 9.698005613 },
		{ label: 'NAMER', value: 5.257716269 },
		{ label: 'PRK', value: 0.01254578 },
		{ label: 'NOR', value: 0.277746793 },
		{ label: 'OCEN', value: 3.240267755 },
		{ label: 'OMN', value: 0.251457286 },
		{ label: 'PAK', value: 6.21734837 },
		{ label: 'PLW', value: 6.444444444 },
		{ label: 'PSE', value: 0.427424212 },
		{ label: 'PAN', value: 8.558407913 },
		{ label: 'PNG', value: 13.62101185 },
		{ label: 'PER', value: 4.315995078 },
		{ label: 'PHL', value: 37.23096275 },
		{ label: 'POL', value: 0.372782939 },
		{ label: 'PRT', value: 0.373362018 },
		{ label: 'PRI', value: 0.440845551 },
		{ label: 'QAT', value: 0.540960452 },
		{ label: 'REU', value: 0.262092238 },
		{ label: 'ROU', value: 2.693570875 },
		{ label: 'RUS', value: 2.491149775 },
		{ label: 'KNA', value: 1.830188679 },
		{ label: 'LCA', value: 23.36612022 },
		{ label: 'VCT', value: 11.12612613 },
		{ label: 'WSM', value: 8.822335025 },
		{ label: 'STP', value: 9.623255814 },
		{ label: 'SAU', value: 0.209402084 },
		{ label: 'SEN', value: 4.029209622 },
		{ label: 'SYC', value: 0.336734694 },
		{ label: 'SLE', value: 11.67784462 },
		{ label: 'SGP', value: 0.425223983 },
		{ label: 'SVK', value: 0.315008246 },
		{ label: 'SVN', value: 0.405964406 },
		{ label: 'SLB', value: 5.253731343 },
		{ label: 'SOM', value: 0.002719679 },
		{ label: 'ZAF', value: 12.09855186 },
		{ label: 'KOR', value: 0.237306003 },
		{ label: 'ESP', value: 0.435415196 },
		{ label: 'LKA', value: 7.290658413 },
		{ label: 'SDN', value: 18.25672109 },
		{ label: 'SUR', value: 39.47160069 },
		{ label: 'SWE', value: 0.423973695 },
		{ label: 'SYR', value: 0.029408319 },
		{ label: 'TWN', value: 0.315554808 },
		{ label: 'TZA', value: 29.59055254 },
		{ label: 'THA', value: 19.55720564 },
		{ label: 'TGO', value: 15.06842366 },
		{ label: 'TON', value: 6.403846154 },
		{ label: 'TTO', value: 52.42939068 },
		{ label: 'TUN', value: 24.7574177 },
		{ label: 'TUR', value: 19.85029366 },
		{ label: 'UKR', value: 8.950697822 },
		{ label: 'ARE', value: 0.525534746 },
		{ label: 'GBR', value: 0.442973493 },
		{ label: 'USA', value: 0.812815117 },
		{ label: 'URY', value: 26.75332178 },
		{ label: 'VEN', value: 23.54576378 },
		{ label: 'VNM', value: 11.53604528 },
		{ label: 'ESH', value: 7.068728522 },
		{ label: 'OWID_WRL', value: 8.008550858 },
		{ label: 'YEM', value: 10.00401207 },
		{ label: 'ZWE', value: 35.83919426 }
		];

  
	let tooltipText = '';

	const margin = { top: 10, right: 50, bottom: 60, left: 60 }; // Increase margin for axis labels
	const width = 10000 - margin.left - margin.right; // Adjust width
	const height = 700 - margin.top - margin.bottom; // Adjust height

	let svg;

	onMount(() => {
		svg = d3
		.select('#bar-chart-container')
		.append('svg')
		.attr('width', width + margin.left + margin.right)
		.attr('height', height + margin.top + margin.bottom)
		.append('g')
		.attr('transform', `translate(${margin.left},${margin.top})`);

		const x = d3
		.scaleBand()
		.domain(data.map(d => d.label))
		.range([0, width])
		.padding(0.1);

		const y = d3
		.scaleLinear()
		.domain([0, d3.max(data, d => d.value)])
		.nice()
		.range([height, 0]);

		svg
		.append('g')
		.attr('class', 'x-axis')
		.attr('transform', `translate(0,${height})`)
		.call(d3.axisBottom(x))
		.append('text')
		.attr('x', width / 2)
		.attr('y', 40) // Adjusted position
		.attr('text-anchor', 'middle')
		.text('Country')
		.style('font-family', 'futura');


		svg.append('g').attr('class', 'y-axis').call(d3.axisLeft(y));

		svg
		.append('g')
		.selectAll('.bar')
		.data(data)
		.enter()
		.append('rect')
		.attr('class', 'bar')
		.attr('x', d => x(d.label))
		.attr('y', d => y(d.value))
		.attr('width', x.bandwidth())
		.attr('height', d => height - y(d.value))
		.attr("fill", 'steelblue')
		.on('mouseover', (event, d) => {
			tooltipText = `${d.label}: ${d.value}kg`;
			d3.select(event.target).attr('fill', 'orange'); // Change color on hover
		})
		.on('mouseout', (event, d) => {
			tooltipText = '';
			d3.select(event.target).attr('fill', 'steelblue'); // Reset color on mouseout
		});

		// Add title
		// svg
		// .append('text')
		// .attr('x', width / 2)
		// .attr('y', -margin.top / 2)
		// .attr('text-anchor', 'middle')
		// .style('font-size', '1.5em')
		// .text('How Does the Global Mismanaged Plastic per Capita differ by Country?');

		// Add Y-axis label
		svg
		.append('text')
		.attr('transform', 'rotate(-90)')
		.attr('x', -height / 2)
		.attr('y', -margin.left + 20) // Adjusted position
		.attr('text-anchor', 'middle')
		.text('Mismanaged plastic waste per capita (kg per year)')
		.style('font-size', '1.2em')
		.style('font-family', 'futura');
	});
	</script>

	<style>
	.bar {
		fill: steelblue;
	}

	#tooltip {
		position: sticky;
		background: transparent;
		padding: 5px;
		pointer-events: none;
		left: 150px;
		top: 200px;
		width: 150px; /* Adjust width as needed */
		height: 50px; /* Adjust height as needed */
		font-family: 'Futura';
	}


	</style>

	<div id="bar-chart-container"  style="position: relative; overflow: auto;">
	<div id="tooltip">{tooltipText}</div>
	</div>
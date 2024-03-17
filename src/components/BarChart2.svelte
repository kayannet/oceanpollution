<!-- <script>
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

	const margin = { top: 10, right: 0, bottom: 60, left: 60 }; // Increase margin for axis labels
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
	</div> -->

	<script>
		import { onMount } from 'svelte';
		import * as d3 from 'd3';
		import { csvParse } from 'd3';
	
		let data = [
			{'label': 'AFR', 'full': 'Africa', 'value': 10.46592827}, {'label': 'ALB', 'full': 'Albania', 'value': 24.23915307}, {'label': 'DZA', 'full': 'Algeria', 'value': 17.75899473}, {'label': 'AGO', 'full': 'Angola', 'value': 7.445278869}, {'label': 'ATG', 'full': 'Antigua and Barbuda', 'value': 6.463917526}, {'label': 'ARG', 'full': 'Argentina', 'value': 10.40191152}, {'label': '', 'full': 'Asia', 'value': 8.667235444}, {'label': 'AUS', 'full': 'Australia', 'value': 0.20894338}, {'label': 'BHS', 'full': 'Bahamas', 'value': 5.686375321}, {'label': 'BHR', 'full': 'Bahrain', 'value': 0.635588056}, {'label': 'BGD', 'full': 'Bangladesh', 'value': 6.268108387}, {'label': 'BRB', 'full': 'Barbados', 'value': 3.038327526}, {'label': 'BEL', 'full': 'Belgium', 'value': 0.19793743}, {'label': 'BLZ', 'full': 'Belize', 'value': 15.43846154}, {'label': 'BEN', 'full': 'Benin', 'value': 11.29861876}, {'label': 'BIH', 'full': 'Bosnia and Herzegovina', 'value': 16.82853681}, {'label': 'BRA', 'full': 'Brazil', 'value': 15.62046908}, {'label': 'BRN', 'full': 'Brunei', 'value': 1.598152425}, {'label': 'BGR', 'full': 'Bulgaria', 'value': 0.445285714}, {'label': 'BFA', 'full': 'Burkina Faso', 'value': 15.61429064}, {'label': 'KHM', 'full': 'Cambodia', 'value': 15.01152423}, {'label': 'CMR', 'full': 'Cameroon', 'value': 22.36814036}, {'label': 'CAN', 'full': 'Canada', 'value': 0.630483013}, {'label': 'CPV', 'full': 'Cape Verde', 'value': 6.487272727}, {'label': 'CHL', 'full': 'Chile', 'value': 1.623417054}, {'label': 'CHN', 'full': 'China', 'value': 8.559308412}, {'label': 'COL', 'full': 'Colombia', 'value': 1.697570472}, {'label': 'COM', 'full': 'Comoros', 'value': 69.51586369}, {'label': 'COG', 'full': 'Congo', 'value': 12.13361829}, {'label': 'CRI', 'full': 'Costa Rica', 'value': 1.139263074}, {'label': 'CIV', 'full': "Cote d'Ivoire", 'value': 11.33934751}, {'label': 'HRV', 'full': 'Croatia', 'value': 4.247941889}, {'label': 'CYP', 'full': 'Cyprus', 'value': 0.698081735}, {'label': 'COD', 'full': 'Democratic Republic of Congo', 'value': 15.78193592}, {'label': 'DNK', 'full': 'Denmark', 'value': 0.067567568}, {'label': 'DJI', 'full': 'Djibouti', 'value': 10.56365503}, {'label': 'DMA', 'full': 'Dominica', 'value': 15.02777778}, {'label': 'DOM', 'full': 'Dominican Republic', 'value': 18.06667287}, {'label': 'TLS', 'full': 'East Timor', 'value': 13.33642691}, {'label': 'ECU', 'full': 'Ecuador', 'value': 6.262058248}, {'label': 'EGY', 'full': 'Egypt', 'value': 14.29961748}, {'label': 'SLV', 'full': 'El Salvador', 'value': 3.361171367}, {'label': 'GNQ', 'full': 'Equatorial Guinea', 'value': 6.934365782}, {'label': 'ERI', 'full': 'Eritrea', 'value': 24.0457535}, {'label': 'EST', 'full': 'Estonia', 'value': 0.452488688}, {'label': '', 'full': 'Europe', 'value': 1.580226046}, {'label': 'FJI', 'full': 'Fiji', 'value': 4.334831461}, {'label': 'FIN', 'full': 'Finland', 'value': 0.473788865}, {'label': 'FRA', 'full': 'France', 'value': 0.426531552}, {'label': 'GUF', 'full': 'French Guiana', 'value': 0.432989691}, {'label': 'GAB', 'full': 'Gabon', 'value': 2.757017948}, {'label': 'GMB', 'full': 'Gambia', 'value': 14.9467632}, {'label': 'GEO', 'full': 'Georgia', 'value': 0.076807606}, {'label': 'DEU', 'full': 'Germany', 'value': 0.606774669}, {'label': 'GHA', 'full': 'Ghana', 'value': 17.09520679}, {'label': 'GRC', 'full': 'Greece', 'value': 0.430249212}, {'label': 'GRD', 'full': 'Grenada', 'value': 12.11607143}, {'label': 'GLP', 'full': 'Guadeloupe', 'value': 0.405}, {'label': 'GTM', 'full': 'Guatemala', 'value': 17.68972186}, {'label': 'GIN', 'full': 'Guinea', 'value': 11.58852087}, {'label': 'GNB', 'full': 'Guinea-Bissau', 'value': 10.65330557}, {'label': 'GUY', 'full': 'Guyana', 'value': 35.20434227}, {'label': 'HTI', 'full': 'Haiti', 'value': 21.12829619}, {'label': 'HND', 'full': 'Honduras', 'value': 14.97999179}, {'label': 'HKG', 'full': 'Hong Kong', 'value': 0.777434104}, {'label': 'ISL', 'full': 'Iceland', 'value': 0.445427729}, {'label': 'IND', 'full': 'India', 'value': 9.509608}, {'label': 'IDN', 'full': 'Indonesia', 'value': 3.045657286}, {'label': 'IRN', 'full': 'Iran', 'value': 5.981679813}, {'label': 'IRQ', 'full': 'Iraq', 'value': 12.51007377}, {'label': 'IRL', 'full': 'Ireland', 'value': 0.547931176}, {'label': 'ISR', 'full': 'Israel', 'value': 0.711351098}, {'label': 'ITA', 'full': 'Italy', 'value': 0.640842279}, {'label': 'JAM', 'full': 'Jamaica', 'value': 16.84972863}, {'label': 'JPN', 'full': 'Japan', 'value': 0.281286458}, {'label': 'JOR', 'full': 'Jordan', 'value': 12.31686795}, {'label': 'KAZ', 'full': 'Kazakhstan', 'value': 2.92393941}, {'label': 'KEN', 'full': 'Kenya', 'value': 5.514455815}, {'label': 'KIR', 'full': 'Kiribati', 'value': 0.627118644}, {'label': 'KWT', 'full': 'Kuwait', 'value': 0.627525553}, {'label': 'LVA', 'full': 'Latvia', 'value': 0.500786576}, {'label': 'LBN', 'full': 'Lebanon', 'value': 6.800175029}, {'label': 'LSO', 'full': 'Lesotho', 'value': 14.30164706}, {'label': 'LBR', 'full': 'Liberia', 'value': 8.087907636}, {'label': 'LBY', 'full': 'Libya', 'value': 27.81983178}, {'label': 'LTU', 'full': 'Lithuania', 'value': 0.375724638}, {'label': 'MDG', 'full': 'Madagascar', 'value': 0.936260151}, {'label': 'MYS', 'full': 'Malaysia', 'value': 25.491518}, {'label': 'MDV', 'full': 'Maldives', 'value': 0.11299435}, {'label': 'MLT', 'full': 'Malta', 'value': 0.588636364}, {'label': 'MHL', 'full': 'Marshall Islands', 'value': 0.271186441}, {'label': 'MTQ', 'full': 'Martinique', 'value': 0.369680851}, {'label': 'MRT', 'full': 'Mauritania', 'value': 4.594785683}, {'label': 'MUS', 'full': 'Mauritius', 'value': 0.235433071}, {'label': 'MEX', 'full': 'Mexico', 'value': 3.375352731}, {'label': 'MCO', 'full': 'Monaco', 'value': 0.128205128}, {'label': 'MNE', 'full': 'Montenegro', 'value': 0.025477707}, {'label': 'MAR', 'full': 'Morocco', 'value': 8.101776705}, {'label': 'MOZ', 'full': 'Mozambique', 'value': 14.30652704}, {'label': 'MMR', 'full': 'Myanmar', 'value': 8.038338422}, {'label': 'NAM', 'full': 'Namibia', 'value': 8.373547094}, {'label': 'NLD', 'full': 'Netherlands', 'value': 0.890975025}, {'label': 'NZL', 'full': 'New Zealand', 'value': 0.358352498}, {'label': 'NIC', 'full': 'Nicaragua', 'value': 16.93583868}, {'label': 'NGA', 'full': 'Nigeria', 'value': 9.698005613}, {'label': '', 'full': 'North America', 'value': 5.257716269}, {'label': 'PRK', 'full': 'North Korea', 'value': 0.01254578}, {'label': 'NOR', 'full': 'Norway', 'value': 0.277746793}, {'label': '', 'full': 'Oceania', 'value': 3.240267755}, {'label': 'OMN', 'full': 'Oman', 'value': 0.251457286}, {'label': 'PAK', 'full': 'Pakistan', 'value': 6.21734837}, {'label': 'PLW', 'full': 'Palau', 'value': 6.444444444}, {'label': 'PSE', 'full': 'Palestine', 'value': 0.427424212}, {'label': 'PAN', 'full': 'Panama', 'value': 8.558407913}, {'label': 'PNG', 'full': 'Papua New Guinea', 'value': 13.62101185}, {'label': 'PER', 'full': 'Peru', 'value': 4.315995078}, {'label': 'PHL', 'full': 'Philippines', 'value': 37.23096275}, {'label': 'POL', 'full': 'Poland', 'value': 0.372782939}, {'label': 'PRT', 'full': 'Portugal', 'value': 0.373362018}, {'label': 'PRI', 'full': 'Puerto Rico', 'value': 0.440845551}, {'label': 'QAT', 'full': 'Qatar', 'value': 0.540960452}, {'label': 'REU', 'full': 'Reunion', 'value': 0.262092238}, {'label': 'ROU', 'full': 'Romania', 'value': 2.693570875}, {'label': 'RUS', 'full': 'Russia', 'value': 2.491149775}, {'label': 'KNA', 'full': 'Saint Kitts and Nevis', 'value': 1.830188679}, {'label': 'LCA', 'full': 'Saint Lucia', 'value': 23.36612022}, {'label': 'VCT', 'full': 'Saint Vincent and the Grenadines', 'value': 11.12612613}, {'label': 'WSM', 'full': 'Samoa', 'value': 8.822335025}, {'label': 'STP', 'full': 'Sao Tome and Principe', 'value': 9.623255814}, {'label': 'SAU', 'full': 'Saudi Arabia', 'value': 0.209402084}, {'label': 'SEN', 'full': 'Senegal', 'value': 4.029209622}, {'label': 'SYC', 'full': 'Seychelles', 'value': 0.336734694}, {'label': 'SLE', 'full': 'Sierra Leone', 'value': 11.67784462}, {'label': 'SGP', 'full': 'Singapore', 'value': 0.425223983}, {'label': 'SVK', 'full': 'Slovakia', 'value': 0.315008246}, {'label': 'SVN', 'full': 'Slovenia', 'value': 0.405964406}, {'label': 'SLB', 'full': 'Solomon Islands', 'value': 5.253731343}, {'label': 'SOM', 'full': 'Somalia', 'value': 0.002719679}, {'label': 'ZAF', 'full': 'South Africa', 'value': 12.09855186}, {'label': 'KOR', 'full': 'South Korea', 'value': 0.237306003}, {'label': 'ESP', 'full': 'Spain', 'value': 0.435415196}, {'label': 'LKA', 'full': 'Sri Lanka', 'value': 7.290658413}, {'label': 'SDN', 'full': 'Sudan', 'value': 18.25672109}, {'label': 'SUR', 'full': 'Suriname', 'value': 39.47160069}, {'label': 'SWE', 'full': 'Sweden', 'value': 0.423973695}, {'label': 'SYR', 'full': 'Syria', 'value': 0.029408319}, {'label': 'TWN', 'full': 'Taiwan', 'value': 0.315554808}, {'label': 'TZA', 'full': 'Tanzania', 'value': 29.59055254}, {'label': 'THA', 'full': 'Thailand', 'value': 19.55720564}, {'label': 'TGO', 'full': 'Togo', 'value': 15.06842366}, {'label': 'TON', 'full': 'Tonga', 'value': 6.403846154}, {'label': 'TTO', 'full': 'Trinidad and Tobago', 'value': 52.42939068}, {'label': 'TUN', 'full': 'Tunisia', 'value': 24.7574177}, {'label': 'TUR', 'full': 'Turkey', 'value': 19.85029366}, {'label': 'UKR', 'full': 'Ukraine', 'value': 8.950697822}, {'label': 'ARE', 'full': 'United Arab Emirates', 'value': 0.525534746}, {'label': 'GBR', 'full': 'United Kingdom', 'value': 0.442973493}, {'label': 'USA', 'full': 'United States', 'value': 0.812815117}, {'label': 'URY', 'full': 'Uruguay', 'value': 26.75332178}, {'label': 'VEN', 'full': 'Venezuela', 'value': 23.54576378}, {'label': 'VNM', 'full': 'Vietnam', 'value': 11.53604528}, {'label': 'ESH', 'full': 'Western Sahara', 'value': 7.068728522}, {'label': 'OWID_WRL', 'full': 'World', 'value': 8.008550858}, {'label': 'YEM', 'full': 'Yemen', 'value': 10.00401207}, {'label': 'ZWE', 'full': 'Zimbabwe', 'value': 35.83919426}
			];
	
	
		
	let tooltipText = '';
	
	const margin = { top: 10, right: 0, bottom: 60, left: 60 }; // Increase margin for axis labels
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
			tooltipText = `${d.full}: ${d.value}kg`;
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
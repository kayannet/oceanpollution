<script>
  import { onMount } from 'svelte';
  import * as d3 from 'd3';

  let data = [
    { year: 1950, value: 2000000 },
    { year: 1951, value: 2000000 },
    { year: 1952, value: 2000000 },
    { year: 1953, value: 3000000 },
    { year: 1954, value: 3000000 },
    { year: 1955, value: 4000000 },
    { year: 1956, value: 5000000 },
    { year: 1957, value: 5000000 },
    { year: 1958, value: 6000000 },
    { year: 1959, value: 7000000 },
    { year: 1960, value: 8000000 },
    { year: 1961, value: 9000000 },
    { year: 1962, value: 11000000 },
    { year: 1963, value: 13000000 },
    { year: 1964, value: 15000000 },
    { year: 1965, value: 17000000 },
    { year: 1966, value: 20000000 },
    { year: 1967, value: 23000000 },
    { year: 1968, value: 27000000 },
    { year: 1969, value: 32000000 },
    { year: 1970, value: 35000000 },
    { year: 1971, value: 38000000 },
    { year: 1972, value: 44000000 },
    { year: 1973, value: 51000000 },
    { year: 1975, value: 46000000 },
    { year: 1976, value: 54000000 },
    { year: 1977, value: 59000000 },
    { year: 1978, value: 64000000 },
    { year: 1979, value: 71000000 },
    { year: 1980, value: 70000000 },
    { year: 1981, value: 72000000 },
    { year: 1982, value: 73000000 },
    { year: 1983, value: 80000000 },
    { year: 1984, value: 86000000 },
    { year: 1985, value: 90000000 },
    { year: 1986, value: 96000000 },
    { year: 1987, value: 104000000 },
    { year: 1988, value: 110000000 },
    { year: 1989, value: 114000000 },
    { year: 1990, value: 120000000 },
    { year: 1991, value: 124000000 },
    { year: 1992, value: 132000000 },
    { year: 1993, value: 137000000 },
    { year: 1994, value: 151000000 },
    { year: 1995, value: 156000000 },
    { year: 1996, value: 168000000 },
    { year: 1997, value: 180000000 },
    { year: 1998, value: 188000000 },
    { year: 1999, value: 202000000 },
    { year: 2000, value: 213000000 },
    { year: 2001, value: 218000000 },
    { year: 2002, value: 231000000 },
    { year: 2003, value: 241000000 },
    { year: 2004, value: 256000000 },
    { year: 2005, value: 263000000 },
    { year: 2006, value: 280000000 },
    { year: 2007, value: 295000000 },
    { year: 2008, value: 281000000 },
    { year: 2009, value: 288000000 },
    { year: 2010, value: 313000000 },
    { year: 2011, value: 325000000 },
    { year: 2012, value: 338000000 },
    { year: 2013, value: 352000000 },
    { year: 2014, value: 367000000 },
    { year: 2015, value: 381000000 },
    { year: 2016, value: 400050000 },
    { year: 2017, value: 420052500 },
    { year: 2018, value: 441055140 },
    { year: 2019, value: 459746020 }
  ];

  let tooltipText = '';

  const margin = { top: 60, right: 10, bottom: 80, left: 150 };
  const width = 1000 - margin.left - margin.right;
  const height = 600 - margin.top - margin.bottom;

  let svg;

  onMount(() => {
    svg = d3
      .select('#line-chart-container')
      .append('svg')
      .attr('width', width + margin.left + margin.right)
      .attr('height', height + margin.top + margin.bottom)
      .append('g')
      .attr('transform', `translate(${margin.left},${margin.top})`);

    const x = d3
      .scaleLinear()
      .domain(d3.extent(data, d => d.year))
      .range([0, width]);

    const y = d3
      .scaleLinear()
      .domain([0, d3.max(data, d => d.value) + 50000000])
      .range([height, 0]);

    const line = d3
      .line()
      .x(d => x(d.year))
      .y(d => y(d.value));

    svg
      .append('path')
      .datum(data)
      .attr('fill', 'none')
      .attr('stroke', 'steelblue')
      .attr('stroke-width', 2)
      .attr('d', line);

    svg
      .selectAll('circle')
      .data(data)
      .enter()
      .append('circle')
      .attr('cx', d => x(d.year))
      .attr('cy', d => y(d.value))
      .attr('r', 3)
      .attr('fill', 'steelblue')
      .style('font-family', 'Futura')
      .on('mouseover', (event, d) => {
        tooltipText = `Year: ${d.year}, Value: ${d.value/1000000} million tons`;
        d3.select(event.target).attr('r', 5);
        d3.select(event.target).attr('fill', 'darkred');

      })
      .on('mouseout', () => {
        tooltipText = '';
        d3.select(event.target).attr('r', 3);
        d3.select(event.target).attr('fill', 'steelblue');

      });
      

   
    svg
      .append('g')
      .attr('transform', `translate(0,${height})`)
      .call(d3.axisBottom(x).tickFormat(d3.format('d')))
      .append('text')
      .attr('x', width / 2)
      .attr('y', margin.bottom - 10)
      .attr('fill', '#000')
      // .attr('font-weight', 'bold')
      .attr('text-anchor', 'middle')
      .text('Year')
      .style('font-family', 'Futura')
      .style('font-size', '20px')
;

    svg.append('g').call(d3.axisLeft(y));

    svg
      .append('text')
      .attr('transform', 'rotate(-90)')
      .attr('x', -height / 2)
      .attr('y', -margin.left + 20)
      .attr('dy', '1em')
      .attr('fill', '#000')
      // .attr('font-weight', '')
      .attr('text-anchor', 'middle')
      .text('Annual Plastic Production (tons)')
      .style('font-family', 'Futura')
;
  });

  const xOffset = -300; // adjust the horizontal offset
  const yOffset = -200; // adjust the vertical offset
  function handleMousemove(event) {
    const tooltip = document.getElementById('tooltip');
    if (tooltip) {
      tooltip.style.left = `${event.clientX + xOffset}px`;
      tooltip.style.top = `${event.clientY + yOffset}px`;
    }
  }
</script>

<style>
  #tooltip {
    position: absolute;
		background: transparent;
		padding: 5px;
		pointer-events: none;
		left: 150px;
		top: 200px;
		width: 300px; /* Adjust width as needed */
		height: 50px; /* Adjust height as needed */
		font-family: 'Futura';
    
  }
</style>

<!-- <h1>How Has Global Plastic Production Increased Over the Years?</h1> -->

<div id="line-chart-container" on:mousemove={handleMousemove}>
  <div id="tooltip">{tooltipText}</div>
</div>
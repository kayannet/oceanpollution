<script>
    import { onMount } from 'svelte';
    import * as d3 from 'd3';
  
    let data = [
      { x: 0, y: 30 },
      { x: 1, y: 40 },
      { x: 2, y: 45 },
      { x: 3, y: 55 },
      { x: 4, y: 60 },
      { x: 5, y: 65 }
    ];
  
    onMount(() => {
      // Set the dimensions and margins of the plot
      const margin = {top: 20, right: 30, bottom: 30, left: 40};
      const width = 500 - margin.left - margin.right;
      const height = 500 - margin.top - margin.bottom;
  
      // Append the SVG object to the div called "chart"
      const svg = d3.select("#chart")
        .append("svg")
          .attr("width", width + margin.left + margin.right)
          .attr("height", height + margin.top + margin.bottom)
        .append("g")
          .attr("transform", `translate(${margin.left}, ${margin.top})`);
  
      // X scale and axis
      const x = d3.scaleLinear()
        .domain(d3.extent(data, d => d.x))
        .range([0, width]);
      svg.append("g")
        .attr("transform", `translate(0, ${height})`)
        .call(d3.axisBottom(x));
  
      // Y scale and axis
      const y = d3.scaleLinear()
        .domain([0, d3.max(data, d => d.y)])
        .range([height, 0]);
      svg.append("g")
        .call(d3.axisLeft(y));
  
      // Add the line
      svg.append("path")
        .datum(data)
        .attr("fill", "none")
        .attr("stroke", "steelblue")
        .attr("stroke-width", 2)
        .attr("d", d3.line()
          .x(d => x(d.x))
          .y(d => y(d.y)));


          // Add event listeners for interactivity
    svg.selectAll(".dot")
        .data(data)
        .enter().append("circle")
        .attr("class", "dot")
        .attr("cx", d => x(d.x))
        .attr("cy", d => y(d.y))
        .attr("r", 5)
        .style("fill", "steelblue")
        .on("mouseover", handleMouseOver)
        .on("mouseout", handleMouseOut);
    
        svg.selectAll(".text-label")
        .data(data)
        .enter().append("text")
        .attr("class", "text-label")
        .attr("x", d => x(d.x))
        .attr("y", d => y(d.y) - 10) // Adjust the y position as needed
        .text(d => `(${d.x}, ${d.y})`)
        .attr("text-anchor", "middle")
        .attr("font-size", "10px")
        .attr("fill", "black");

        function handleMouseOver(d, i) {
        d3.select(this)
            .transition()
            .duration(200)
            .attr("r", 8);
        }

        function handleMouseOut(d, i) {
        d3.select(this)
            .transition()
            .duration(200)
            .attr("r", 5);
        }
    });
  </script>
  
  <div id="chart" ></div>
  
  <style>
    /* Add any necessary styles for your chart container */
    #chart {
      width: 100%;
      height: 0;
    }
    /* .chart.visible {
    opacity: 1;
    visibility: visible;
  } */
  </style>
  
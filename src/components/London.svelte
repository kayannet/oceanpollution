<script>
  import { onMount } from 'svelte';
  import * as d3 from 'd3';

  let data2015 = [
    {
      "": 0,
      "entity": "Americas (excl. USA)",
      "year": 2000,
      "recycled": 4.721963,
      "incinerated": 1.2200574,
      "littered/mismanaged": 32.702644,
      "landfilled": 61.355328
    },
    {
      "": 20,
      "entity": "Asia (excl. China and India)",
      "year": 2000,
      "recycled": 3.8260822,
      "incinerated": 10.439383,
      "littered/mismanaged": 36.90847,
      "landfilled": 48.82608
    },
    {
      "": 40,
      "entity": "China",
      "year": 2000,
      "recycled": 4.7811875,
      "incinerated": 8.821573,
      "littered/mismanaged": 60.803017,
      "landfilled": 25.594213
    },
    {
      "": 60,
      "entity": "Europe",
      "year": 2000,
      "recycled": 4.4350724,
      "incinerated": 14.542094,
      "littered/mismanaged": 12.974696,
      "landfilled": 68.048134
    },
    {
      "": 80,
      "entity": "India",
      "year": 2000,
      "recycled": 5.072351,
      "incinerated": 1.6886452,
      "littered/mismanaged": 68.140015,
      "landfilled": 25.098991
    },
    {
      "": 100,
      "entity": "Middle East & North Africa",
      "year": 2000,
      "recycled": 2.8385525,
      "incinerated": 0.4083155,
      "littered/mismanaged": 46.085022,
      "landfilled": 50.668125
    },
    {
      "": 120,
      "entity": "Oceania",
      "year": 2000,
      "recycled": 3.8013995,
      "incinerated": 9.345559,
      "littered/mismanaged": 11.801067,
      "landfilled": 75.05197
    },
    {
      "": 140,
      "entity": "Sub-Saharan Africa",
      "year": 2000,
      "recycled": 3.0122259,
      "incinerated": 0,
      "littered/mismanaged": 69.32282,
      "landfilled": 27.664953
    },
    {
      "": 160,
      "entity": "United States",
      "year": 2000,
      "recycled": 2.3450744,
      "incinerated": 15.26663,
      "littered/mismanaged": 7.976449,
      "landfilled": 74.41184
    },
    {
      "": 180,
      "entity": "World",
      "year": 2000,
      "recycled": 3.7033863,
      "incinerated": 10.872603,
      "littered/mismanaged": 26.019512,
      "landfilled": 59.4045
    }
  ]

  let data2019 = [
  {
    "": 19,
    "entity": "Americas (excl. USA)",
    "year": 2019,
    "recycled": 9.554245,
    "incinerated": 1.1592599,
    "littered/mismanaged": 29.180883,
    "landfilled": 60.10561
  },
  {
    "": 39,
    "entity": "Asia (excl. China and India)",
    "year": 2019,
    "recycled": 8.351267,
    "incinerated": 18.513683,
    "littered/mismanaged": 33.74583,
    "landfilled": 39.38922
  },
  {
    "": 59,
    "entity": "China",
    "year": 2019,
    "recycled": 12.801141,
    "incinerated": 23.762764,
    "littered/mismanaged": 27.052067,
    "landfilled": 36.384026
  },
  {
    "": 79,
    "entity": "Europe",
    "year": 2019,
    "recycled": 12.384406,
    "incinerated": 37.74739,
    "littered/mismanaged": 5.667553,
    "landfilled": 44.200645
  },
  {
    "": 99,
    "entity": "India",
    "year": 2019,
    "recycled": 13.333093,
    "incinerated": 4.1608157,
    "littered/mismanaged": 46.214355,
    "landfilled": 36.29173
  },
  {
    "": 119,
    "entity": "Middle East & North Africa",
    "year": 2019,
    "recycled": 5.4478326,
    "incinerated": 0.6075314,
    "littered/mismanaged": 39.797066,
    "landfilled": 54.14757
  },
  {
    "": 139,
    "entity": "Oceania",
    "year": 2019,
    "recycled": 6.8709826,
    "incinerated": 11.508256,
    "littered/mismanaged": 6.7546487,
    "landfilled": 74.86611
  },
  {
    "": 159,
    "entity": "Sub-Saharan Africa",
    "year": 2019,
    "recycled": 5.7193336,
    "incinerated": 0.5053036,
    "littered/mismanaged": 63.607426,
    "landfilled": 30.167952
  },
  {
    "": 179,
    "entity": "United States",
    "year": 2019,
    "recycled": 4.488883,
    "incinerated": 19.078592,
    "littered/mismanaged": 3.552523,
    "landfilled": 72.880005
  },
  {
    "": 199,
    "entity": "World",
    "year": 2019,
    "recycled": 9.292344,
    "incinerated": 19.048033,
    "littered/mismanaged": 22.45448,
    "landfilled": 49.205143
  }
]

let selectedEntity = data2019[0].entity;

const margin = { top: 40, right: 50, bottom: 60, left: 60 }; // Increase the margins
const width = 700 - margin.left - margin.right; // Increase the width
const height = 500 - margin.top - margin.bottom; // Increase the height

let svg;

onMount(() => {
  svg = d3.select('#chart')
    .append('svg')
    .attr('width', width + margin.left + margin.right)
    .attr('height', height + margin.top + margin.bottom)
    .append('g')
    .attr('transform', `translate(${margin.left},${margin.top})`);

  updateChart();
});

function updateChart() {
  const entityData2019 = data2019.find(d => d.entity === selectedEntity);
  const entityData2015 = data2015.find(d => d.entity === selectedEntity);
  const categories = ['recycled', 'incinerated', 'littered/mismanaged', 'landfilled'];

  const x = d3.scaleBand()
    .domain(categories)
    .range([0, width])
    .padding(0.1);

  const y = d3.scaleLinear()
    .domain([0, d3.max(categories.map(cat => Math.max(entityData2015[cat], entityData2019[cat])))])
    .nice()
    .range([height, 0]);

  const xAxis = d3.axisBottom(x);
  const yAxis = d3.axisLeft(y);

  svg.selectAll('*').remove();

  svg.append('g')
    .attr('transform', `translate(0,${height})`)
    .call(xAxis);

  svg.append('g')
    .call(yAxis);

  const barWidth = x.bandwidth() / 2; // Half of the bandwidth


  svg.selectAll('.bar2015')
    .data(categories)
    .enter()
    .append('rect')
    .attr('class', 'bar bar2015')
    .attr('x', (cat, i) => x(cat) - barWidth + 55)
    .attr('y', cat => y(entityData2015[cat]))
    .attr('width', x.bandwidth() / 2)
    .attr('height', cat => height - y(entityData2015[cat]))
    .attr('fill', 'steelblue')
    .each(function(cat) {
      svg.append("text")
        .attr("class", "bar-label")
        .attr("x", x(cat) - barWidth + 55 + x.bandwidth() / 4)
        .attr("y", y(entityData2015[cat]) - 5)
        .attr("text-anchor", "middle")
        .text(entityData2015[cat].toFixed(2) + "%")
        .style("fill", "white")
        .style("font-size", "12px")
        .style("font-family", "Futura");
    });;


  svg.selectAll('.bar2019')
    .data(categories)
    .enter()
    .append('rect')
    .attr('class', 'bar bar2019')
    .attr('x', (cat, i) => x(cat) - barWidth + 120 )
    .attr('y', cat => y(entityData2019[cat]))
    .attr('width', x.bandwidth() / 2)
    .attr('height', cat => height - y(entityData2019[cat]))
    .attr('fill', 'orange')
    .each(function(cat) {
      svg.append("text")
        .attr("class", "bar-label")
        .attr("x", x(cat) - barWidth + 120 + x.bandwidth() / 4)
        .attr("y", y(entityData2019[cat]) - 5)
        .attr("text-anchor", "middle")
        .text(entityData2019[cat].toFixed(2) + "%")
        .style("fill", "white")
        .style("font-size", "12px")
        .style("font-family", "Futura");
    });

    svg.append("text")
      .attr("transform", "rotate(-90)")
      .attr("y", 0 - margin.left + 8)
      .attr("x", 0 - (height / 2))
      .attr("dy", "1em")
      .style("text-anchor", "middle")
      .text("Percentage (%)")
      .style("font-family", "Futura");

    // Append x-axis label
    svg.append("text")
      .attr("x", width / 2)
      .attr("y", height + margin.top + 10 ) // Adjusted position for x-axis label
      .style("text-anchor", "middle")
      .text("Waste Disposal Methods")
      .style("font-family", "Futura")
      .style("fill", "Futura");


    svg.selectAll('.tick text')
      .style("font-family", "Futura")
      .style("font-size", "12px") // Adjust font size as needed

    // Modify the font of y-axis ticks
    svg.selectAll('.tick text')
      .style("font-family", "Futura")
      .style("font-size", "12px"); // Adjust font size as needed
  
}

  
</script>
<p class = 'barChartTitle2'> Waste Management Comparison (2000 vs 2019) </p>

<select bind:value={selectedEntity} on:change={updateChart} style="position: relative; top: 70px; left: 700px;">
  {#each data2019 as { entity }}
    <option value={entity}>{entity}</option>
  {/each}
</select>

<div style="position: relative;">
  <div class="legend" style="position: absolute; top: 10px; left: 40px;">
    <svg width="100" height="20" style="margin-bottom: 5px;">
      <rect x="0" y="0" width="20" height="20" fill="steelblue" />
      <text x="25" y="15" font-family='Futura' fill='white'>2000</text>
    </svg>

    <svg width="110" height="20" style="margin-bottom: 5px;">
      <rect x="0" y="0" width="20" height="20" fill="orange" />
      <text x="25" y="15" font-family='Futura' fill='white'>2019</text>
    </svg>
  </div>

  <div id="chart"></div>

</div>




<style>
  .legend{
    margin-top: 40px;
    margin-left: 40px;
  }
  .barChartTitle2{
        top: 40px;
        left: 50px;
        position: relative;
        font-size: 30px;
        font-family: Futura;
    }
  
  
</style>

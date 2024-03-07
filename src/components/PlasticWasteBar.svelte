<script>
    const data = [
        {country: 'Philippines', Share_of_global_plastics_emitted_to_ocean: 36.38 },
        {country: 'India' , Share_of_global_plastics_emitted_to_ocean: 12.92 },
        {country: 'Malaysia' , Share_of_global_plastics_emitted_to_ocean: 7.46 },
        {country: 'China' , Share_of_global_plastics_emitted_to_ocean: 7.22},
        {country: 'Indonesia' , Share_of_global_plastics_emitted_to_ocean: 5.75 },
    ] 
    let dim = {
        'width': 720, 
        'height':500, 
        'margin':50   
        };

    let svg = d3.select('#chart').append('svg')  
        .attrs(dim);




    document.querySelector("#chart").classList.add("center");

    let scaleX = d3.scaleLinear()
                .domain([0, d3.max(fruits, d => d.count)])
                .nice()
                .range([dim.margin, dim.width - dim.margin])
                .interpolate(d3.interpolateRound)

    let scaleY = d3.scaleBand()
                .domain(fruits.map(d => d.name))
                .range([dim.margin, dim.height - dim.margin])
                .padding(0.1)
                .round(true)

    let color = d3.scaleSequential()
            .domain([0, d3.max(fruits, d=>d.count)])
            .interpolator(d3.interpolateBlues);

    let scaleQuantize = d3.scaleQuantize()
            .domain(d3.extent(fruits, (d)=>d.health))
                .range(['red', 'orange', 'blue', 'lightgreen', 'green']);


    let axisX = d3.axisTop(scaleX);
    let axisY = d3.axisLeft(scaleY);

    svg.append('g')
    .attr('transform', 'translate(0,50)')
    .attr('color', '#fff')
    .call(axisX)


    svg.append('g')
    .attr('transform', 'translate(50,0)')    
    .call(axisY);



    svg.selectAll('rect')    
    .data(fruits)
    .enter()
    .append('rect')
    .attrs({
        'x':(d) =>scaleX(0),
        'y':(d) => scaleY(d.name),
        'width':(d)=>  0,
        'height':(d)=>scaleY.bandwidth(),
        'fill':(d)=>color(d.count)

    })
    .transition().duration(1000).attr('width', (d)=>  scaleX(d.count) - scaleX(0))


    svg.selectAll('circle')
    .data(fruits)
    .enter()
    .append('circle')
    .attrs({
        'cx':(d) => 0,
        'cy':(d) => scaleY(d.name) + 20,
        'r':5,
        'fill':(d) =>scaleQuantize(d.health)
    })
    .transition().duration(1000).attr('cx', (d) =>scaleX(d.count) + 20);


</script>
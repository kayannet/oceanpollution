<script>
    import mapboxgl from 'mapbox-gl';
    import 'mapbox-gl/dist/mapbox-gl.css';
    import { onMount, onDestroy } from 'svelte';
    let map;
    let mapContainer;
    let legend;

    

    mapboxgl.accessToken = "pk.eyJ1Ijoia3F0cmFuIiwiYSI6ImNsc2t6eXQ4czA3dmcyanJ5eWhoaWQxeHIifQ.2kwe8rDh1r-X61ULATh_Jg";
    
    onMount(() => {
        map = new mapboxgl.Map({
                container: mapContainer,
                style: "mapbox://styles/kqtran/cltevc8s500sh01oifnhb6u2z" ,  
                center: [-79.035728, 35.932522], // Chapel Hill Public Library
                zoom: 1.5,
                minZoom: 1.5,
                maxZoom: 1.5,
            });
        
        
        map.on('load', () => {
        // the rest of the code will go in here
        
            const layers = [
            '0-3500',
            '3500-7000000',
            '7000000-90000000',
            '90000000-180000000',
            '180000000-300000000',
            '300000000+',
            ];
            const colors = [
            '#ebecd4',
            '#eef1bc',
            '#b6d5a6',
            '#6fbd6b',
            '#93a6a9',
            '#ad8fea',
            ];
        
            // const legend = document.getElementById('legend');
        
            // layers.forEach((layer, i) => {
            //     const color = colors[i];
            //     const item = document.createElement('div')
            //     const key = document.createElement('span');
            //     key.className = 'legend-key';
            //     key.style.backgroundColor = color;
        
            //     const value = document.createElement('span');
            //     value.innerHTML = `${layer}`;
            //     item.appendChild(key);
            //     item.appendChild(value);
            //     legend.appendChild(item)
            // }); 
        
        
            map.on('mousemove', (event) => {
            const countries = map.queryRenderedFeatures(event.point, {
                layers: ['Share_of_global_plastics_emitted_to_ocean']
            });
            const Share_of_global_plastics_emitted_to_ocean = countries.length ? countries[0].properties.Share_of_global_plastics_emitted_to_ocean : undefined;
            const truncatedShare = Share_of_global_plastics_emitted_to_ocean !== undefined ? parseFloat(Share_of_global_plastics_emitted_to_ocean).toFixed(2) : undefined;

            document.getElementById('pd').innerHTML = truncatedShare !== undefined 
                ? `<h3> ${countries[0].properties.Entity}</h3><p><strong>${truncatedShare}</strong>%</p>`
                : `<h3> Hover over a country!</h3>`;
        });
        
        
            map.getCanvas().style.cursor = 'default';
        
        });
    });
    
    // onDestroy(() => {
    //     map.remove();
    // });
    
    
    
    </script>

    <!-- <div class="map-wrap">
        <div class="map" bind:this={mapContainer} />
    </div> -->
    <main>
        <div class="map-wrap">
            <div class="map" bind:this={mapContainer}></div>
            <div class="map-overlay" id="features">


                <h1 class = "title">Share of Global Plastics <br>
                    Emitted to the Ocean (2019)</h1>
                
                <div id="pd">
                    <h3 class = 'sub'> Hover over a country!</h3>
                </div>
            </div>
            
        </div>
    </main>


    

  <style>
    body {
        margin: 0;
        padding: 0;
    }
    
    h2,
    h3 {
        margin: 8px;
        font-size: 18px;
    }
    
    p {
        left: 8px;
        margin: 8px;
        font-size: 10px;
    }
    #pd{
        margin: 8px;

        font-size: 20px;
        /* margin: 5x; */
    }

    .sub{
        margin: -2px;
        font-size: 23px;
    }
    

    .title {
        font-size: 23px;
        margin-left: 10px;
    }
    
    .map-wrap {
        position: absolute;
        top: 200px;
        width: 100%;
        height: 100%; /* Adjust height as needed */
        border: none !important; /* Override border */

    }

    .map {
        position:absolute;
        top: -200px;
        left: 0;
        width: 100%;
        height: 100%;
        margins: 0;
        padding: 0; /* Ensure no padding */
        border: none !important; /* Override border */


    }
    
    /**
    * Set rules for how the map overlays
    * (information box and legend) will be displayed
    * on the page. */
   
    .map-overlay {
        position: absolute;
        bottom: 30px;
        left: 0;
        background: transparent;
        margin-right: 10px;
        font-family: Helvectia, sans-serif;
        overflow: auto;
        /* border-radius: 3px; */
        padding: 5px;
        height: auto;
        border: none !important; /* Override border */

    }


    /* title */
    #features {
        top: -200px;
        height: 10px;
        margin-top: 10px;
        width: fit-content;
        height: fit-content;
        border: none !important; /* Override border */

    }
    
    #legend {
        padding: 15px;
        box-shadow: 0 1px 2px rgba(0 0 0 0.1);
        line-height: 20px;
        /* height: 250px; */
        margin-bottom: -19px;
        max-width: fit;
        width: fit;
    }
    
    /* .legend-key {
        display: inline-block;
        border-radius: 20%;
        width: 15px;
        height: 15px;
        margin-right: 5px;
    } */
   
  </style>
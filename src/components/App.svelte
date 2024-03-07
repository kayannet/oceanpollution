
<script>
    import Test from './Test.svelte';
    import swimmingFish from '$lib/img/swimming_fish.png'

    // import data from ".static/global-plastic-production.js";
    // import BarChart from "./BarChart_test.svelte";
    import Bchart from "./bgraph1.svelte";
    // import Bcharthtml from "./barg.html";
    import data from "./data.js";
    import BarChart from "./bgraph1.svelte";
    import Globe from "./Globe.svelte";
    
	let scroll;
	let speed = 4
    let width, height;

    const threshold = 1000
</script>


<svelte:window bind:scrollY={scroll} />



<h1>{scroll}</h1>

<div class = "container" style:background="#879ec4">

    <section style="min-height: {16 * 500}px">


        <!-- TITLE -->
        <div class="box" style:transform={`translate3d(0, ${scroll * 0.4}px, 0)`} style:background="#879ec4">
            <h2>PLASTIC POLLUTION</h2>
            <p class = "subtitle">BY: KAYANNE TRAN AND KETKI CHAKRADEO</p>
            <a class = "writeUpLink" href="https://docs.google.com/document/d/1uq1zLNTzoAXbKIo428ckIYjbZcrKFskz5TGQw68XJc0/edit">Write Up Link</a>
        </div>

        <!-- FIRST TEXT SECTION -->
        <div class="box" style:transform={`translate3d(0, ${scroll * 0.2}px, 0)`} style:background = '#879ec4'> 
            <p class = "text">

                Plastic is a synthetic material that can be molded when soft and formed into a solid shape.
                It's strength, durability, and flexibility revolutionalized modern technology. <br>
                Plastic is also easy and cheap to manufacture, hence the volume of it in nearly all of our products/
            </p>
        </div>

         <!-- SWIMMING FISH -->
        <div class="box" style:transform={`translate3d(${scroll * 0.3}px, ${scroll * -0.3}px, ${scroll * -2}px)`} style:background="">
            <div class = fish1>
                <img src = {swimmingFish} alt = 'swimming_fish' style="max-width: 100%; max-height: 100%;">
            </div>
        </div>
        <div class="box" style:transform={`translate3d(${scroll * 0.7}px, ${scroll * -0.5}px, ${scroll * -2}px)`} style:background="">
            <div class = fish1>
                <img src = {swimmingFish} alt = 'swimming_fish' style="max-width: 100%; max-height: 100%;">
            </div>
        </div>

        <!-- SECOND TEXT SECTION -->

        <div>        
            <p class = 'text2'> However, the mass production and use of plastic has detrimental effects 
                <br> on our environment and marine life. It's durability and strength also means
                 <br> that it is not biodegradable, and can remain in our environment for hundred of years.
                 <br>
                <br> This is plastic pollution.
                </p>
        </div>


        <div> 
            <img class = 'fishPlastic' src="https://www.pewtrusts.org/-/media/post-launch-images/2018/09/plastics-oceans-0924_5/16x9_m.jpg?mw=2580&hash=C6292C51D1D0CF90405428698D78740C" alt="Clipart" >
            <img class = 'birdPlastic' src="https://www.pewtrusts.org/-/media/post-launch-images/2018/09/plastics_ocean_0924_2/16x9_s.jpg?mw=2580&hash=7CE7C88529DE596B4656917EFB77292E" alt="Clipart" >

            <p class = 'text25'> Due to its sheer volume, improper plastic disposal has become a 
                <br> major environmental issue. Millions of tons of plastic debris is
                <br> dumped into our oceans daily, so fish, turtles, birds, and other 
                <br> species can ingest or become entangled in the plastic, causing 
                <br> suffocation, starvation, and drowning. </p>
        </div>
        <!-- FIRST VISUALIZATION -->
        <div class = 'barChartTitleContainer1'>
            <p class = 'barChartTitle1'> Mismanaged plastic waste per capita (kg per year), 2019 </p>
        </div>
        <div class = 'barChart1' style:background="transparent">
            <BarChart {data} />
        </div>

        <div>
            <p class="caption1"> Here, we can see the average kilograms of mismanged plastic waste per person in  
                <br> 2019 from each country. 
                <br>
                <br> Plastic has become such a staple in our lives that 
                <br> it's easy to forget that it's not a natural material for wildlife too. People easily forget 
                <br> about things that are out of sight, but the volume of plastic waste in our oceans is 
                <br> leading to mass endangerment for hundreds of species.
             </p>

        </div>

        <!-- SECOND VISUALIZATION -->
        <div class = 'globe-container'   style:background="#edede9">
            <div class = 'globe'>
                <Globe />

            </div>
        </div>





        

        
        <!-- FIRST VISUALIZATION -->
        <!-- <div class="box" style="transform: translate3d(0, ${scroll * -2}px, 0); background: red;">
            <BarChart />
            <p class="caption1">VIS 1 HERE (about global plastic production over time)</p>
        </div>
         -->
        

        <!-- <div class="box" id = 'pic1' style:transform={`translate3d(0, ${scroll * -0.4}px,0)`} style:background="red">
            <div class = fish1>
                <img src = "https://www.greenpeace.org/usa/wp-content/uploads/2018/04/GP0STR1T7_Medium_res-970xcenter-c-default.jpg" alt = 'Plastic Pollution' style="max-width: 100%; max-height: 100%;">
            </div>
        </div> -->


        <!-- SECOND VISUALIZATION -->
        <!-- <div class="box" style:transform={`translate3d(0, ${scroll * -0.5}px, 0)`} style:background="teal">
            <Test  />
            <p class = caption1> VIS 2 HERE (choropleth)</p>

        </div> -->

       
        
        <!-- <div class="box" style:transform={`translate3d(0, ${scroll * -0.5}px, 0)`} style:background = "yellow"/> -->
        <!-- <div class="box"  style:transform={`translate3d(0, ${scroll * -0.5}px, 0)`} style:background = "yellow"/> -->
        <div class="box" />
        <div class="box" />
        <div class="box" />
        <div class="box" />
        <div class="box" />
        <div class="box" />
        <div class="box" />
        <div class="box" />
        <div class="box" />
    </section>
</div>


<style>
    
    .container {
        width: 100vw; /* Set the width to 100% of the viewport width */
        overflow-x: hidden; /* Hide horizontal overflow */
    }

    section {
        /* margin: 0px; */
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        height: 100vh;
        width: 100vw;
        overflow-y: auto; /* Enable vertical scrolling */
        overflow-x: hidden; /* Hide horizontal overflow */


    }
	h1 {
		position: fixed;
        text-align: center;
		z-index: 10;
	}
    h2{
        top: 20%;
        left: 50%;
        transform: translate(-50%, -50%); /* Translate the text to center it properly */
		position: relative;
        font-family: 'Franklin Gothic Medium';
        font-size: 80px;
        color: white;
        text-align: center;
		z-index: 10;
        padding: 0px;
    }
    /* p{
        top: 20%;
        left: 50%;
        transform: translate(-50%, -50%); 
		position: relative;
        font-family: 'Franklin Gothic Medium';
        font-size: 25px;
        color: white;
        text-align: center;
		z-index: 10;

    } */
    .subtitle{
        top: 0%;
        left: 50%;
        transform: translate(-50%, -50%); /* Translate the text to center it properly */
		position: relative;
        font-family: 'Helvetica';
        font-size: 25px;
        color: white;
        text-align: center;
		z-index: 10;
    }
    .text{
        top: 30%;
        left: 50%;
        transform: translate(-50%, -50%); /* Translate the text to center it properly */
		position: relative;
        font-family: 'Futura';
        font-size: 25px;
        color: white;
        text-align: center;
		z-index: 11;
        margin: 5px;
    }
    .text2{
        top: -500%;
        left: 5%;
        transform: translate(-50%, -50%); /* Translate the text to center it properly */
		position: relative;
        font-family: 'Futura';
        font-size: 25px;
        color: white;
        text-align: left;
		z-index: 11;
    }
    .text25{
        top: -900px;
        right: -125%;
        transform: translate(-50%, -50%); /* Translate the text to center it properly */
		position: relative;
        font-family: 'Futura';
        font-size: 25px;
        color: white;
        text-align: left;
		z-index: 11;
    }
    .caption1{
        top: -1090px;
        left: 1050px;
        transform: translate(-50%, -50%); /* Translate the text to center it properly */
        /* position: -webkit-sticky; */
		position: relative;
        font-family: 'Futura';
        background-color: transparent; /* Ensure it stands out against the chart */
        margin: 5px;

        font-size: 25px;
        color: white;
        text-align: Left;
		z-index: 1;
    }
    .fishPlastic{
        top: -150% ;
        left: -42%;
        max-width: 500px;
        max-height: 500px;
        position: relative;
        z-index: 9;
    }
    .birdPlastic{
        top: -150% ;
        left: -40%;
        max-width: 500px;
        max-height: 500px;
        position: relative;
        z-index: 9;
    }
    .barChart1{
        height: 100%;
		width:  100%;
		margin-bottom: 0rem;
        position: relative;
        /* margin: 0; */
        z-index: 9;
        overflow: auto;


        top: -800px;
        left: -500px;
        position: relative;
        max-width: 1050px;
        max-height: 1000px;
        border-style: solid;
    }
    .barChartTitle1{
        top: -580%;
        left: -48%;
        position: relative;
        font-size: 40px;
        font-family: Futura;

    }
    .globe-container {
        position: relative;
        top: -12%;
        left: -20%;
        width: 1000px; /* Adjust the width as needed */
        height: 200%; /* Make it full height */
        background: gray; /* Background color */
        z-index: 9; /* Ensure it's on top of other elements */
        overflow-y: auto; /* Allow scrolling if content exceeds height */
        border-style: solid;
        border-radius: 1%;
        border-width: 4px;
        border-color: black;
    }

    .globe {
        width: 100%;
        height: 100%;
    }

	.box {
		/* --size: 500px; */
		height: 100%;
		width:  100%;
		margin-bottom: 0rem;
        position: relative;
        /* margin: 0; */
        z-index: 9;


	}

    .fish1{
        position: relative;
        z-index: 8;
        background: "";
    }
    .writeUpLink{
        top: 0%;
        left: 45%;
        transform: translate(-50%, -50%); /* Translate the text to center it properly */
		position: relative;
        font-family: 'Helvetica';
        font-size: 25px;
        color: white;
        text-align: center;
		z-index: 10;

    }
  
    /* .vis2{
        position: absolute;
        top: 1760px;
        left: 800px;
        z-index: 9;


    } */
</style>
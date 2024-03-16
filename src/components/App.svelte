
<script>
    import Test from './Test.svelte';
    import swimmingFish from '$lib/img/swimming_fish.png'
    import swimmingFish2 from '$lib/img/swimming_fish2.png'
    import swimmingFish3 from '$lib/img/swimming_fish3.png'



    // import data from ".static/global-plastic-production.js";
    // import BarChart from "./BarChart_test.svelte";
    import Bchart from "./bgraph1.svelte";
    // import Bcharthtml from "./barg.html";
    import data from "./data.js";
    import BarChart from "./bgraph1.svelte";
    import Globe from "./Globe.svelte";
    import PWFate from "./London.svelte"
    import BarChart2 from './BarChart2.svelte';
    import LineGraph from './LineGraph.svelte';
    
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
        <div class="box" style:transform={`translate3d(0, ${scroll * 0.4}px, 0)`} >
            <h2>PLASTIC POLLUTION</h2>
            <p class = "subtitle">BY: KAYANNE TRAN AND KETKI CHAKRADEO</p>
            <!-- <a class = "writeUpLink" href="https://docs.google.com/document/d/1uq1zLNTzoAXbKIo428ckIYjbZcrKFskz5TGQw68XJc0/edit">Write Up Link</a> -->
        </div>

        <!-- FIRST TEXT SECTION -->
        <div class="box" style:transform={`translate3d(0, ${scroll * 0.2}px, 0)`} > 
            <p class="text">
                Plastic is a synthetic material that can be molded when soft and formed into a solid shape.
                It's strength, durability, and flexibility revolutionalized modern technology. <br>
                Plastic is also easy and cheap to manufacture, hence the volume of it in nearly all of our products.
               
            </p>

        </div>

         <!-- SWIMMING FISH -->
        <div class="fishbox" style:transform={`translate3d(${scroll * 0.3}px, ${scroll * -0.3}px, ${scroll * -2}px)`} style:background="">
            <div class = fish1>
                <img src = {swimmingFish} alt = 'swimming_fish' style="max-width: 100%; max-height: 100%;">
            </div>
        </div>
        <div class="fishbox" style:transform={`translate3d(${scroll * 0.7}px, ${scroll * -0.5}px, ${scroll * -2}px)`} style:background="">
            <div class = fish1>
                <img src = {swimmingFish} alt = 'swimming_fish' style="max-width: 100%; max-height: 100%;">
            </div>
        </div>

         <!-- SECOND VISUALIZATION -->
        <div class = 'lineGraphContainer1'  style:transform={`translate3d(0, ${scroll * -0.5}px, 0)`}>
            <p class = 'lineGraphTitle1'> Global Plastic Production, 1950 - 2019 </p>
            <div class = 'lineGraph1' style:background="transparent">
                <LineGraph />
            </div>
            <div class = "caption1Box" style:transform={`translate3d(0, ${scroll * -0.5}px, 0)`}>
                <p class="caption1">  The convenience of plastic has revolutionized industries, 
                    offering lightweight, durable, and versatile materials that have enhanced packaging, 
                    transportation, and everyday products. Its widespread use has improved food preservation,
                     reduced transportation costs, and enabled the development of innovative medical devices, 
                     contributing to advancements in healthcare and improving overall quality of life. 
                </p>
    
            </div>
        </div>

        <!-- SECOND TEXT SECTION -->
        

        <div class="box2" style:background = 'transparent'>        
            <p class = 'text'> 
                However, the mass production and use of plastic has detrimental effects on our environment and marine life. It's durability and strength also means that it is not biodegradable, and can remain in our environment for hundred of years. This is plastic pollution.
            </p>
        </div>



        <!-- FISH TRANSITION -->
        <div style:transform={`translate3d(${scroll * -0.4}px, ${scroll * -0.5}px, ${scroll * -0.1}px)`} style:background="">
            <div class = fish2>
                <img src = {swimmingFish2} alt = 'swimming_fish2' style="max-width: 100%; max-height: 100%;">
            </div>
        </div>
        <div style:transform={`translate3d(${scroll * -0.5}px, ${scroll * -0.7}px, ${scroll * -0.1}px)`} style:background="">
            <div class = fish2>
                <img src = {swimmingFish2} alt = 'swimming_fish2' style="max-width: 100%; max-height: 100%;">
            </div>
        </div>

        <div class = "box3" style:transform={`translate3d(0, ${scroll * -0.2}px, 0)`}> 
            <div class = 'imageBox'>
                <img class = 'fishPlastic' src="https://www.pewtrusts.org/-/media/post-launch-images/2018/09/plastics-oceans-0924_5/16x9_m.jpg?mw=2580&hash=C6292C51D1D0CF90405428698D78740C" alt="Clipart" >
                <img class = 'birdPlastic' src="https://www.pewtrusts.org/-/media/post-launch-images/2018/09/plastics_ocean_0924_2/16x9_s.jpg?mw=2580&hash=7CE7C88529DE596B4656917EFB77292E" alt="Clipart" >
                <img class = 'sealPlastic' src="https://t4.ftcdn.net/jpg/03/53/08/59/360_F_353085965_uVdDmO2uLFDwZDQ5Rw4W38vrXJyYK9n4.jpg" alt="Clipart" >
            </div>
            
            <p class = 'text25'> This pollution harms marine life through entanglement, ingestion, and habitat destruction. 
                Marine animals often suffer injuries or death due to entanglement in plastic debris, while 
                ingestion of plastics disrupts their feeding habits and can cause internal harm. 
                This pollution also affects ecosystems, leading to chemical contamination, bioaccumulation of toxins, and altered habitats.. </p>

            <div class = 'imageBox2'>
                <img class = 'turtlePlastic' src="https://media.istockphoto.com/id/1141999585/photo/underwater-global-problem-with-plastic-rubbish.jpg?s=612x612&w=0&k=20&c=LnHPndHoRgWZpR4Uu2E7n0fZJNuLqUEkHLYoc8Lo29o=" alt="Clipart" >
                <img class = 'bearPlastic' src="https://www.plasticsoupfoundation.org/wp-content/uploads/2019/11/dierenleed.jpg" alt="Clipart" >
                <img class = 'dolphinPlastic' src="https://i.natgeofe.com/n/824d5de0-6e47-456c-9c8e-6027a6eb716e/animals-plastic-nationalgeographic_1230842.jpg" alt="Clipart" >
            </div>
        </div>
        
        
       

        <div class = 'barChartTitleContainer1'>
            <p class = 'barChartTitle1'> Mismanaged plastic waste per capita (kg per year), 2019 </p>
        <div class = 'barChart1' style:background="transparent">
            <BarChart2/>
        </div>

        <div class = "caption2Box">
            <p class="caption2">  Here, we can see the average kilograms of mismanged 
                <br> plastic waste per person in 2019 from each country.
                <br> Mismanaged waste is defined by trash that is not 
                <br> recycled, incinerated, or kept in sealed landfills. 
             </p>
             <p class = "caption25">
                While certain countries have a minimal mismanaged waste value, many others have very 
                large amounts, which emphasizes that this issue is a global one. The disparity in waste 
                management capabilities highlights the need for a coordinated global effort to address 
                the challenges posed by plastic pollution. Countries with lower levels of mismanaged waste 
                can share their best practices and provide support to those facing greater difficulties in 
                managing their waste streams.
             </p>

        </div>

        </div>



       


        <!-- SECOND VISUALIZATION -->
        <!-- <div class="barChartContainer1">
            <p class='barChartTitle1'>Mismanaged plastic waste per capita (kg per year), 2019</p>
            <div class='barChartScrollContainer'>
                    <BarChart2 />
            </div>
        </div> -->
        
        
        <!-- <div class = 'barChartTitleContainer1'>
            <p class = 'barChartTitle1'> Mismanaged plastic waste per capita (kg per year), 2019 </p>

            <div class = 'barChart1' style:background="transparent">
                <BarChart2 />
            </div>

        <div>
            <p class="caption1">  Here, we can see the average kilograms of mismanged plastic waste per person in  
                2019 from each country. 
                
                Plastic has become such a staple in our lives that such that 
                it's easy to overlook its unnatural presence in the natural world. The reality is 
                that plastic is not native to wildlife habitats. Unfortunately, out of sight often
                means out of mind, but the staggering volume of plastic waste accumulating in our oceans 
                poses a grave threat to hundreds of species, pushing them 
                towards endangerment and extinction.
             </p>

        </div>

        </div> -->
        
        <div class = 'globe-container' style:transform={`translate3d(0, ${scroll * -0.4}px, 0)`}   > <!--style:/background="#edede9" -->
            <div class = 'globe'>
                <Globe />
            </div>
            <div class="map-overlay">
                <!-- Manually created legend key with SVG -->
                <h3 class = "legendTitle"> Legend (percent of plastic waste that is emitted to the ocean) </h3>
                <div class = "legend">
                    <svg width="100" height="20" style="margin-bottom: 5px;">
                        <rect x="0" y="0" width="20" height="20" fill="#f8f8f1" />
                        <text x="25" y="15"> &lt; 0.5% </text>
                    </svg>

                    <svg width="110" height="20" style="margin-bottom: 5px;">
                        <rect x="0" y="0" width="20" height="20" fill="#b8d5b8" />
                        <text x="25" y="15">0.5-1.0%</text>
                    </svg>

                    <svg width="110" height="20" style="margin-bottom: 5px;">
                        <rect x="0" y="0" width="20" height="20" fill="#7bb791" />
                        <text x="25" y="15">1.0-1.5%</text>
                    </svg>

                    <svg width="110" height="20" style="margin-bottom: 5px;">
                        <rect x="0" y="0" width="20" height="20" fill="#6ac5c8" />
                        <text x="25" y="15">1.5-2.0%</text>
                    </svg>

                    <svg width="110" height="20" style="margin-bottom: 5px;">
                        <rect x="0" y="0" width="20" height="20" fill="#7dbcd9" />
                        <text x="25" y="15">2.0-2.5%</text>
                    </svg>

                    <svg width="110" height="20" style="margin-bottom: 5px;">
                        <rect x="0" y="0" width="20" height="20" fill="#3f7b97" />
                        <text x="25" y="15">2.5-5.0%</text>
                    </svg>
                    <svg width="110" height="20" style="margin-bottom: 5px;">
                        <rect x="0" y="0" width="20" height="20" fill="#464285" />
                        <text x="25" y="15">5.0-10.0%</text>
                    </svg>
                    <svg width="110" height="20" style="margin-bottom: 5px;">
                        <rect x="0" y="0" width="20" height="20" fill="#a165a4" />
                        <text x="25" y="15">10.0-15.0%</text>
                    </svg>
                    <svg width="100" height="20" style="margin-bottom: 5px;">
                        <rect x="" y="0" width="20" height="20" fill="#cd2d85" />
                        <text x="25" y="15">15.0% &gt;</text>
                    </svg>
                </div>


            </div>

            <div class = "caption3Box" style:transform={`translate3d(0, ${scroll * -0.5}px, 0)`}>
                <p class="caption3">  As we zoom into different regions on the map, it becomes 
                    apparent that certain areas are particularly significant contributors to 
                    plastic waste in the oceans. Countries in Asia, especially densely populated
                    ones with rapidly growing economies like China, Indonesia, and the Philippines,
                    are major sources of plastic pollution due to their large populations and 
                    industrial activities. 
                      
                      <br>
                      <br>
                    Coastal nations, islands, and regions surrounded 
                    by water also face challenges with waste management, as marine litter can
                    easily enter the oceans through waterways and shorelines. 

                    <br>
                    <br>
                    Furthermore, regions with inadequate waste infrastructure and limited recycling 
                    capabilities often struggle to manage their plastic waste effectively, leading to 
                    higher rates of mismanaged waste and plastic pollution.

                </p>
    
            </div>
        </div>



        <!-- <div class = "caption3Box" style:transform={`translate3d(0, ${scroll * -0.4}px, 0)`}>
            <p class="caption3"> Here, we can see the average kilograms of mismanged plastic waste per person in  
                2019 from each country. 
                
                Plastic has become such a staple in our lives that such that 
                it's easy to overlook its unnatural presence in the natural world. The reality is 
                that plastic is not native to wildlife habitats. Unfortunately, out of sight often
                means out of mind, but the staggering volume of plastic waste accumulating in our oceans 
                poses a grave threat to hundreds of species, pushing them 
                towards endangerment and extinction.
             </p>
        </div> -->

        <div class = 'fishbox3' style:transform={`translate3d( ${scroll * 0.25}px, 0, 0)`}>
            <img src = {swimmingFish3} alt = 'swimming_fish3' style="max-width: 100%; max-height: 100%;">
        </div>

        <div class = "text3box">
            <p class="text3">  

                As the problem increases, countries must begin taking preventaive measures before plastic completely destroys our Earth

            </p>
        </div>

    
       
        

  

        
        


        <!-- THIRD VISUALIZATION-->
        <div class = 'barChartTitleContainer2'>
            <div class = 'barChart2' style:background="transparent">
                <PWFate/>
            </div>

            <div class = 'caption4Box'>
                <p class="caption4">  Since 2000, there has been an overall decrease in mismanaged waste.
                    Factors such as population growth, urbanization, industrialization, and changes in 
                    consumption patterns can influence waste generation rates and the management of plastic waste.
                     Efforts to reduce mismanaged waste require sustained commitment and investment in waste management 
                     systems, recycling facilities, public education, and policies that promote sustainable practices.

                </p>
    
            </div>
            
        </div>

            <div class = 'conclusionBox'>
            <p class = 'conclusion'>
                It's crucial to continue monitoring and addressing plastic pollution comprehensively on a global scale, 
                recognizing that progress in waste management and pollution reduction is an ongoing endeavor that requires 
                collaboration among governments, industries, communities, and individuals worldwide. If not for ourselves, 
                then we must take action for the future generations to come after us.
            </p>
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
    body {
    overflow-x: hidden;
    width: 100vw;
    }

    .container {
        width: 100vw;
        display: flex;
        overflow-x: hidden;


    }

    section {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        height: 100vh;
        max-width: 100vw;
        overflow-y: auto; /* Enable vertical scrolling */
        /* overflow-x: hidden; */ /* Remove this line */
    }
	h1 {
		position: fixed;
        text-align: center;
		z-index: 10;
        color: #879ec4;
	}
    h2{
        top: 20%;
        left: 50%;
        transform: translate(-50%, -50%); /* Translate the text to center it properly */
		position: relative;
        font-family: 'Futura';
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
        top: -10%;
        left: 50%;
        transform: translate(-50%, -50%); /* Translate the text to center it properly */
		position: relative;
        font-family: 'Futura';
        font-size: 20px;
        color: white;
        text-align: center;
		z-index: 10;
    }
    .text{
        top: 200px;
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
        display: flex;
        top: 500px;
        left: 50%;
        transform: translate(-50%, -50%); /* Translate the text to center it properly */
		position: relative;
        font-family: 'Futura';
        font-size: 25px;
        color: white;
        text-align: center;
		z-index: 11;
    }
    .text25{
        display: flex;
        top: -340px;
        left: 50%;
        transform: translate(-50%, -50%); /* Translate the text to center it properly */
		position: relative;
        font-family: 'Futura';
        font-size: 25px;
        color: white;
        text-align: center;
		z-index: 11;
    }

    .caption1, .caption2, .caption25, .caption3, .caption4, .text3, .conclusion {
        display: flex;
        top: 0;
        left: 0;
        /* position: -webkit-sticky; */
		position: relative;
        font-family: 'Futura';
        background-color: transparent; /* Ensure it stands out against the chart */
        margin-top: 20px;

        font-size: 25px;
        color: white;
        text-align: center;
		z-index: 1;
    }
    .caption2{
        display: flex;
        top: -500px;
        left: 700px;
        transform: translate(-50%, -50%); /* Translate the text to center it properly */
		position: relative;
        font-family: 'Futura';
        font-size: 25px;
        color: white;
        text-align: center;
		z-index: 11;
    }
    .caption25{
        top:-200px;
    }
    .text3box{
        position: relative;
        top: -400px;
        max-width: 100vw;

    }
    .caption2Box{
        display: flex;
        flex-direction: column;
        justify-content: center; /* Center-align images horizontally */
        align-items: center; /* Center-align images vertically */

        position: relative;
        top: 10px;
        left: 0;
        width: 90%;
        background-color: transparent;
        max-width: 100vw;


    }


    .caption3Box{
        display: flex;
        flex-direction: column;
        justify-content: center; /* Center-align images horizontally */
        align-items: center; /* Center-align images vertically */

        position: relative;
        top: 1900px;
        left: 780px;
        max-height: 50%;
        max-width: 40%;
        background-color: transparent;

    }

    .caption4Box{
        display: flex;
        flex-direction: column;
        justify-content: center; /* Center-align images horizontally */
        align-items: center; /* Center-align images vertically */

        position: relative;
        top: 50px;
        left: 300px;
        max-height: 50%;
        max-width: 30%;
        background-color: transparent;

    }

    .conclusionBox{
        display: flex;
        flex-direction: column;
        justify-content: center; /* Center-align images horizontally */
        align-items: center; /* Center-align images vertically */

        position: relative;
        top: 90px;
        left: 0;
        width: 90%;
        background-color: transparent;
        max-width: 100vw;

    }

    .caption3{
        margin: 10px;
    }


    .caption1Box{
        display: flex;
        flex-direction: column;
        justify-content: center; /* Center-align images horizontally */
        align-items: center; /* Center-align images vertically */

        position: relative;
        top: 100px;
        left: 600px;
        max-height: 50%;
        max-width: 40%;
        background-color: transparent;

    }

    .fishPlastic, .birdPlastic, .sealPlastic, .turtlePlastic, .bearPlastic, .dolphinPlastic {
        position: relative; /* Position images relative to the imageBox */
        width: 30%; /* Adjust as needed */
        height: auto; /* Maintain aspect ratio */
        max-width: 100%; /* Set a maximum width to prevent excessive scaling */
        max-height: 100%; /* Set a maximum height to prevent excessive scaling */
        z-index: 11;
        
    }

    .fishPlastic {
        top: 0;
        left: 0;
    }

    .birdPlastic, .bearPlastic {
        top: 0; /* Adjust vertical position as needed */
        left:0; /* Adjust horizontal position as needed */
        /* transform: translate(-50%, -50%); */
        margin-left: 20px;

    }

    .sealPlastic, .dolphinPlastic {
        top: 0; /* Adjust vertical position as needed */
        left:0;
        margin-left: 20px;

    }

    .imageBox, .imageBox2{
        display: flex;
        flex-direction: row;
        justify-content: center; /* Center-align images horizontally */
        align-items: center; /* Center-align images vertically */

        position: relative;
        max-height: 200px;
        max-width: 100%;
        background-color: tranparent;
        top: -400px;
        margin-bottom: 50px;
        margin-top: 50px;
    }

    .imageBox2{
        /* top: 20%; */
    }
   

    /* .barChartTitleContainer1{
        display: flex;
        flex-direction: column;
        align-items: center;
        top: -900px;
		height: 100%;
		width:  80%;
		margin-bottom: 0rem;
        position: relative;
        z-index: 9;
        background-color: tranparent;
        overflow-x: scroll;

    } */
    .barChartTitleContainer2{
        display: flex;
        flex-direction: row;
        align-items: center;
        top: 00px;
        left: 100px;
		height: 100%;
		width:  100%;
		margin-bottom: 0rem;
        position: relative;
        z-index: 9;
        background-color: tranparent;
    }

 

    .lineGraphTitle1{
        top: 70px;
        left: -170px;;
        position: relative;
        font-size: 40px;
        font-family: Futura;
    }
    


    .lineGraphContainer1{
        display: flex;
        flex-direction: column;
        align-items: center;
        top: 200px;
        left: -100px;
		height: 100%;
		width:  80%;
		margin-bottom: 0rem;
        position: relative;
        z-index: 7;
        background-color: tranparent;
        overflow-x: visible;        
        
        max-width: 100vw;

        
    }
    .lineGraph1{
        position: relative; /* Position images relative to the imageBox */
        width: 100%; /* Adjust as needed */
        height: 100%; /* Maintain aspect ratio */
        /* Set a maximum height to prevent excessive scaling */
        z-index: 7;
        overflow-x: hidden;
        /* border-style: solid; */
        margin-bottom: 0rem;

        top: 0;
        left: 0;
        align-items: center;
     
    }

    .barChartTitleContainer1{
        display: flex;
        flex-direction: column;
        align-items: center;
        top: -1600px;
		height: auto;
		width:  90%;
		margin-bottom: 0rem;
        position: relative;
        z-index: 9;
        background-color: tranparent;
        max-width: 100vw;

    }
    .barChart1{
        position: relative; /* Position images relative to the imageBox */
        width: 100%; /* Adjust as needed */
        height: 100%; /* Maintain aspect ratio */
        max-width: 1300px;
        max-height: 1000px; /* Set a maximum height to prevent excessive scaling */
        z-index: 11;
        overflow-y: auto;
        margin-bottom: 0rem;

        top: 0;
        left: 0;
        align-items: center;
    }

    .barChartTitle1{
        top: 90px;
        left: 0%;
        position: relative;
        font-size: 40px;
        font-family: Futura;
    }





    







    

    .globe-container {
        /* display: flex; */
        flex-direction: center;
        align-items: center;
        top: 7000px;
        left: 300px;
		height: 65%;
		width:  80%;
		margin-bottom: 0rem;
        position: absolute;
        z-index: 8;
        background-color: transparent;
        max-width: 100vw;

        /* border-style: solid;
        border-radius: 1%;
        border-width: 4px;
        border-color: black;
        overflow-y: fixed; */

        /* display: flex;
        position: relative;
        top: -0%;
        left: -20%;
        width: 1000px; 
        height: 200%; 
        background: gray; 
        z-index: 9; 
        overflow-y: auto;
        border-style: solid;
        border-radius: 1%;
        border-width: 4px;
        border-color: black; */
    }

    .globe {
        /* display: flex; */
        position: relative; /* Position images relative to the imageBox */
        width: 100%; /* Adjust as needed */
        height: 150%; /* Maintain aspect ratio */
        max-width: 1050px;
        max-height: 1000px; /* Set a maximum height to prevent excessive scaling */
        z-index: 8;
        overflow-y: hidden;
        border-style: solid;
        margin-bottom: 0rem;

        top: 0px;
        left: -200px;
        align-items: center;
        border: none; /* Remove border */

    }

    .map-overlay{
        font-family: Futura;
        margin-bottom:0px;
        left: -380px;
        top: 100p;
        position: relative;
        display: flex;
        flex-direction: column;
        z-index: 8;

    }

    .legendTitle, .legend{
        font-family: Futura;
        margin-bottom: 15px;
        font-size: small;
        left: 190px;
        top: -130px;
        position: relative;
        display: flex;
        flex-direction: row;
        z-index: 8;
    }

    
    .fishbox{
        display: flex;
        flex-direction: column;
		height: 100%;
		width:  90%;
		margin-bottom: 0rem;
        position: relative;
        /* margin: 0; */
        z-index: 9;
        top: 300px;
    }
    .fishbox3{
        display: flex;
        flex-direction: column;
		height: 100%;
		width:  40%;
		margin-bottom: 0rem;
        position: relative;
        /* margin: 0; */
        z-index: 9;
        top: -400px;
        left: -1100px;
    }
 

	.box {
		/* --size: 500px; */
        display: flex;
        flex-direction: column;
		height: 100%;
		width:  100vw;
		margin-bottom: 0rem;
        position: relative;
        /* margin: 0; */
        z-index: 9;
	}

    .box2 {
        display: flex;
        flex-direction: column;
        top: -900px;
		height: 100%;
		width:  80%;
		margin-bottom: 0rem;
        position: relative;
        /* margin: 0; */
        z-index: 9;
    }

    .box3{
        display: flex;
        flex-direction: column;
        top: -800px;
		height: 100%;
		width:  80%;
		margin-bottom: 0rem;
        position: relative;
        /* margin: 0; */
        z-index: 9;
        background-color: transparent;
    }

    
    .fish1, .fish2, .fish3{
        position: relative;
        z-index: 8;
        background: "";
    }

    .fish2{
        left: 1300px;
        top: 00px;
        z-index: 13;
    }



    .writeUpLink{
        top: -10%;
        left: 50%;
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
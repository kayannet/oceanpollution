
<script>
    import Test from './Test.svelte';
	let scroll;
	let speed = 4
    let width, height;

    const threshold = 1000


</script>

<svelte:window bind:scrollY={scroll} />

<h1>{scroll}</h1>


<div class = "container" style:background="teal">

    <section style="min-height: {16 * 500}px">
        <div class="box" style:transform={`translate3d(0, ${scroll * 0.4}px, 0)`} style:background="teal">
            <img src="data:image/jpeg;base64,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" alt="Clipart" style="max-width: 100%; max-height: 100%;">
            <h2>PLASTIC POLLUTION</h2>
            <p class = "subtitle">BY: KAYANNE TRAN AND KETKI CHAKRADEO</p>
        </div>
        <div class="box" style:transform={`translate3d(0, ${scroll * 0.2}px, 0)`} style:background = 'teal'> 
            <p class = "text">

                Plastic is a synthetic material that can be molded when soft and formed into a solid shape.
                It is used in nearly all of our products, and it has been an extremely useful invention

                * some short intro*
            </p>


        </div>
        <div class="box"  style:background="teal">
            <Test  />
            <p class = caption1> VIS 1 HERE (about global plastic production over time)</p>

        </div>
        <div>        
            <p class = 'text2'> *something about how plastic is <br> bad for environment and <br> how pollution is so bad</p>
        </div>
<!-- 
        <div class = "vis2" style:background = 'gray'>
            <p> VIS 2</p>
            
        </div> -->



        <div class="box" style:transform={`translate3d(${scroll * 0.3}px, ${scroll * -0.3}px, ${scroll * -2}px)`} style:background="">
            <div class = fish1>
                <img src = "src/img/swimming_fish.png" alt = 'swimming_fish' style="max-width: 100%; max-height: 100%;">
            </div>
        </div>
        <div class="box" style:transform={`translate3d(${scroll * 0.3}px, ${scroll * -0.5}px, ${scroll * -2}px)`} style:background="">
            <div class = fish1>
                <img src = "src/img/swimming_fish.png" alt = 'swimming_fish' style="max-width: 100%; max-height: 100%;">
            </div>
        </div>
        <!-- <div class="box" style:transform={`translate3d(0, ${scroll * -0.5}px, 0)`} style:background = "yellow"/> -->
        <div class="box"  style:transform={`translate3d(0, ${scroll * -0.5}px, 0)`} style:background = "yellow"/>
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
    body{
        background-color: teal;
    }
    img{
        padding: 0;
        margin: 0;
    }
    .container {
        /* margin: 0px; */
        /* background-color: darkblue; Set the background color of the entire website */
    }

    
    section {
        /* margin: 0px; */
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        height: 100vh;
        overflow-y: auto; /* Enable vertical scrolling */

    }
	h1 {
		position: fixed;
        text-align: center;
		z-index: 10;
	}
    h2{
        top: 0;
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
        top: 20%;
        left: 50%;
        transform: translate(-50%, -50%); /* Translate the text to center it properly */
		position: relative;
        font-family: 'Futura';
        font-size: 25px;
        color: white;
        text-align: center;
		z-index: 11;
    }
    .text2{
        top: 1760px;
        left: 300px;
        transform: translate(-50%, -50%); /* Translate the text to center it properly */
		position: absolute;
        font-family: 'Futura';
        font-size: 25px;
        color: white;
        text-align: left;
		z-index: 11;
    }
    .caption1{
        top: 0;
        left: 100%;
        transform: translate(-50%, -50%); /* Translate the text to center it properly */
		position: relative;
        font-family: 'Futura';
        font-size: 25px;
        color: white;
        text-align: Left;
		z-index: 1;
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
	.pin {
		position: fixed;
	}
    
    .fish1{
        position: relative;
        z-index: 8;
        background: "";

    }
    .vis2{
        position: absolute;
        top: 1760px;
        left: 800px;
        z-index: 9;


    }
</style>
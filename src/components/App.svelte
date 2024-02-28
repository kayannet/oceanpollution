
<script>
    import Test from './Test.svelte';
	let scroll;
	let speed = 4
    let width, height;

    const threshold = 1000


</script>

<svelte:window bind:scrollY={scroll} />

<h1>{scroll}</h1>


<div class = "container" background-color="yellow">

    <section style:min-height="{16 * 500}px">
        <div class="box" style:transform={`translate3d(0, ${scroll * 0.4}px, 0)`} style:background="teal">
            <h2>PLASTIC POLLUTION</h2>
            <p> BY: KAYANNE TRAN AND KETKI CHAKRADEO</p>
        </div>
        <div class="box" />
        <div class="box" style:transform={`translate3d(0, ${scroll >= threshold ? threshold * 3 : scroll * -2}px, 0)`} style:background="red">
            <Test  />

        
        
        </div>
        <div class="box" style:transform={`translate3d(0, ${scroll * -3}px, 0)`} style:background="pink"/>
        <div class="box" />
        <div class="box" />
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
        top: 30%;
        left: 50%;
        transform: translate(-50%, -50%); /* Translate the text to center it properly */
		position: relative;
        font-family: 'Franklin Gothic Heavy';
        font-size: 80px;
        color: white;
        text-align: center;
		z-index: 10;
    }
    p{
        top: 20%;
        left: 50%;
        transform: translate(-50%, -50%); /* Translate the text to center it properly */
		position: relative;
        font-family: 'Franklin Gothic Medium';
        font-size: 25px;
        color: white;
        text-align: center;
		z-index: 10;

    }
	.box {
		/* --size: 500px; */
		height: 100%;
		width:  100%;
		background: grey;
		margin-bottom: 1rem;
        position: relative;
        /* margin: 0; */


	}
	
	.pin {
		position: fixed;
	}
</style>
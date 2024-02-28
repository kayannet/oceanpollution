<script>
  import Scroller from "@sveltejs/svelte-scroller";
  import Test from './Test.svelte';
  import { onMount } from 'svelte';
  import * as d3 from 'd3';
  let count, index, offset, progress;  
  let width, height;
  


</script>

<Scroller
  top={0.0}
  bottom={1}
  threshold={0.5}
  bind:count
  bind:index
  bind:offset
  bind:progress
>
  <div 
    class="background" 
    slot="background"
    bind:clientWidth = {width}
    bind:clientHeight = {height}>


    <div class="progress-bars">
      <p>current section: <strong>{index + 1}/{count}</strong></p>
      <progress value={count ? (index + 1) / count : 0} />

      <p>offset in current section</p>
      <progress value={offset || 0} />

      <p>total progress</p>
      <progress value={progress || 0} />
    </div>
  </div>

  <div class="foreground" slot="foreground">
    <section>

      <div>
        <h1> PLASTIC POLLUTION </h1>
        <h2> text introducing our topic</h2>
      </div>


    </section>
    <section>
      <Test {index}  />

    </section>
    <section>This is the third section.</section>
  </div>
</Scroller>


<style>
  .parallax {
    background-image: url('https://www.engineerlive.com/sites/engineerlive/files/stock.jpg');
    min-height: 500px;

    background-attachment: fixed;
    
    
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
  }
  .background {
    width: 100%;
    height: 100vh;
    position: relative;
    outline: green solid 3px;
  }

  .foreground {
    width: 50%;
    margin: 0 auto;
    height: auto;
    position: relative;
    outline: red solid 3px;
  }

  .progress-bars {
    position: absolute;
    background: rgba(170, 51, 120, 0.2) /*  40% opaque */;
    visibility: visible;
  }

  section {
    height: 80vh;
    background-color: rgba(0, 0, 0, 0.2); /* 20% opaque */
    /* color: white; */
    outline: magenta solid 3px;
    text-align: center;
    max-width: 750px; /* adjust at will */
    color: black;
    padding: 1em;
    margin: 0 0 2em 0;
  }
  /* h1,
  h2 {
    position: relative;
    top: 0;
    width: 100%;
    background-color: white;
    padding: 1em;
    margin: 0;
    z-index: 999; /* Ensure it stays above other content */
  .title {
    transition: top 0.3s ease-in-out;
  }
</style>

<div class="parallax"></div>


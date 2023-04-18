<script>
  import { scaleLinear } from "d3-scale";
  import { scaleOrdinal } from "d3-scale";
  import { extent } from "d3-array";
  import { onMount } from "svelte";
  import { draw } from "svelte/transition";
  import { sineInOut } from "svelte/easing";

  import Tooltip from "./tooltip.svelte";

  export let bars;
  let width = 500;
  let div;
  let height = 200;

  const padding = { top: 20, right: 20, bottom: 20, left: 20 };

  const turnOut = bars
    .map((d) => Object.values(d))
    .flat()
    .slice(0, 4);
  const categories = [
    "population",
    "votingAge",
    "registeredVoters",
    "totalVotes",
  ];

  $: xScale = scaleLinear()
    .domain(extent(turnOut))
    .range([padding.left, width - padding.right]);

  const scaleColor = scaleOrdinal()
    .domain(categories)
    .range(["#FAFAFA", "#FAFAFA", "#FAFAFA", "#6CB511"]);

  onMount(resize);

  function resize() {
    ({ width, height } = div.getBoundingClientRect());
  }

  let m = { x: 0, y: 0 };

  function handleMouseover(event) {
    m.x = event.clientX;
    m.y = event.clientY;
    hovered = bars;
  }

  let hovered;
  console.log(turnOut);
</script>

<svelte:window on:resize={resize} />

<div
  class="chart-container"
  bind:this={div}
  on:mouseleave={() => (hovered = null)}
>
  <figure class="chart" on:mouseover={handleMouseover}>
    {#each turnOut as d, i}
      <div
        class="bar"
        style="width:{xScale(d)}px; background-color:{scaleColor(d)};"
      >
        <p class="index">{i + 1}</p>
      </div>
    {/each}
  </figure>
  {#if hovered}
    <Tooltip data={hovered} {width} {xScale} {m} />
  {/if}
</div>

<style>
  .index {
    text-align: center;
    margin-top: 0.2rem;
    font-size: 0.75rem;
    font-family: "Tinos";
    font-weight: 800;
    color: #313131;
  }
  .bar {
    height: 25px;
    margin: 0px;
    border: 2px solid #141414;
  }

  .bar + .bar {
    border-top: 0px;
  }

  .chart-container {
    position: relative;
    margin: 0.5rem auto;
    height: 50%;
    width: 80%;
  }

  .chart {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-top: 0px;
  }
</style>

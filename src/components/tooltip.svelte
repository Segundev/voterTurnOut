<script>
  export let data;
  export let width;
  export let xScale;
  export let m;

  $: x = xScale(m.x);
  $: y = xScale(m.y);

  let toolTipWidth;
  const xNudge = 15;
  const yNudge = 50;

  let xPosition =
    x + toolTipWidth > width ? x - toolTipWidth - xNudge : x + xNudge;
  let yPosition = y;
  console.log(data);
</script>

<div
  class="tooltip"
  style="position: absolute; top: {yPosition}px; left:{xPosition}px ; bottom: {0}px"
  bind:clientWidth={toolTipWidth}
>
  <div class="tooltip_container">
    <div class="wrap">
      <h2 class="tip-head t1">Population</h2>
      <p class="tip-text">
        {data[0].population}
      </p>
    </div>
    <div class="wrap">
      <h2 class="tip-head t2">Voting Age Pop.</h2>
      <p class="tip-text">
        {data[1].votingAge}
      </p>
    </div>
    <div class="wrap">
      <h2 class="tip-head t3">Registered Voters</h2>
      <p class="tip-text">
        {data[2].registeredVoters}
      </p>
    </div>
    <div class="wrap">
      <h2 class="tip-head t4">Total Votes</h2>
      <p class="tip-text">
        {data[3].totalVotes}
      </p>
    </div>
    <div class="wrap">
      <h2 class="tip-head t5">Winner</h2>
      <div>
        <p class="tip-text">{data[5].name}</p>
        <p class="tip-text">{data[4].winPercentage}</p>
      </div>
    </div>
  </div>
</div>

<style>
  .tooltip {
    background-color: #fafafa;
    border: 2.5px solid #141414;
    border-radius: 6px;
    padding: 1rem 1rem;
    text-align: center;
  }
  p,
  h2 {
    margin: 0;
  }

  .wrap {
    padding-bottom: 0.7rem;
  }
  .tip-head {
    font-size: 1rem;
    font-family: "Lato";
    font-weight: 900;
    color: #141414;
    padding-bottom: 0.1rem;
  }

  .tip-text {
    font-size: 0.9rem;
    font-family: "Lato";
    font-weight: 400;
    color: #141414;
  }
</style>

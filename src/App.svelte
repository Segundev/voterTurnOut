<script>
  import Scrolly from "$components/Scrolly.svelte";
  import ParticipationRateChart from "$components/demo.svelte";
  import DashedLine from "$components/dashedLine.svelte";

  import data from "$data/data.js";
  import FunnelChart from "$components/funnelChart.svelte";

  let value;
  const steps = [
    "<p>In <b>2011</b>, Nigeria recorded <b>53.7% voters participation rate</b> with a total votes of <b>39 million</b> out of <b>73 million</b> registered voters </p>",
    "<p>In <b>2015</b>, Nigeria recorded <b>43.7% voters participation rate</b> with a total votes of <b>29 million</b> out of <b>67 million</b> registered voters </p>",
    "<p>In <b>2019</b>, Nigeria recorded <b>34.8% voters participation rate</b> with a total votes of <b>28 million</b> out of <b>82 million</b> registered voters </p>",
    "<p>In <b>2023</b>, Nigeria recorded <b>26.7% voters participation rate</b> with a total votes of <b>25 million</b> out of <b>93 million</b> registered voters </p>",
  ];
</script>

<main>
  <div class="text first-text">
    <p>Only 3 out of 10 eligible voters voted on the 25th of February</p>
  </div>

  <div class="text">
    <p>
      The number of voters who participate in an election greatly influences the
      outcome. Several media outlets and research companies predicted the
      results of the recently held election before it took place, with the
      expectation of a high turnout. The majority of polls favoured Mr. Peter
      Obi, the candidate of the Labour Party. However, only 24.9 million out of
      93.47 million people voted in the recently held presidential and National
      Assembly elections.
    </p>
  </div>

  <div class="text">
    <p>
      Bola Ahmed Tinubu won the election with 9 million votes out of a voting
      population of 121 million. It was expected that 11 million first-time
      registered voters would have a positive effect on turnout on election day.
      Moreover, 40 percent of registered voters were between the ages of 18 and
      34.
    </p>
  </div>

  <div class="text">
    <p>
      Voter turnout or participation rate, which is typically known as the share
      of total vote cast over registered voters or the voting-age population,
      has been on a relatively downward trend over the years.
    </p>
  </div>

  <div class="text">
    <p>
      Since 2007, less than half of the voting-age population has participated
      in the electoral process. The recently concluded general election recorded
      the lowest turnout since 1999, with a mere 26.72 percent voter
      participation.
    </p>
  </div>

  <DashedLine />

  <div class="section-container">
    <div class="steps-container">
      <Scrolly bind:value>
        {#each steps as text, i}
          <div class="step" class:active={value === i}>
            <div class="step-content">{@html text}</div>
          </div>
        {/each}
        <div class="spacer" />
      </Scrolly>
    </div>
    <div class="sticky">
      <ParticipationRateChart />
    </div>
  </div>
</main>
<div class="chart">
  <div class="funnelsection-wrapper">
    <div class="wrap">
      <div>
        <p>Population</p>
      </div>
      <div>
        <p>Voting Age Population</p>
      </div>
      <div>
        <p>Registered Voters</p>
      </div>
      <div>
        <p class="votes">Total Votes</p>
      </div>
    </div>
    <div class="chart-main flex">
      <div>
        <h4>2003 Election</h4>
        <FunnelChart bars={data[2003]} />
      </div>
      <div>
        <h4>2007 Election</h4>
        <FunnelChart bars={data[2007]} />
      </div>
      <div>
        <h4>2011 Election</h4>
        <FunnelChart bars={data[2011]} />
      </div>
      <div>
        <h4>2015 Election</h4>
        <FunnelChart bars={data[2015]} />
      </div>
      <div>
        <h4>2019 Election</h4>
        <FunnelChart bars={data[2019]} />
      </div>
      <div>
        <h4>2023 Election</h4>
        <FunnelChart bars={data[2023]} />
      </div>
    </div>
  </div>
</div>

<DashedLine />

<main>
  <div class="text">
    <p>
      Compared to how each state performed with the outcome of the 2019
      election, only 8 states (Edo, Ogun, Kwara, FCT, Enugu, Osun, Abia, Benue,
      Plateau, and Lagos) recorded an increase in the total number of votes
      casted. Participation rate reduced in all states nationwide except Lagos,
      where voter participation increased by a mere 0.66 percent. Majority of
      the North Western states recorded a low voter turnout when compared to
      2019.
    </p>
  </div>

  <div class="text">
    <p>
      One of the reasons for low voter turnout was the inefficiency of INEC
      officials. At various polling stations, officials arrived late, resulting
      in cases where voters were not allowed to vote before the close of polling
      units at 2:30 p.m. Even though the election continued till late in the
      night at some polling units, not all accredited voters were able to carry
      out their civic responsibility. 51,120 eligible voters in Rivers State
      were unable to vote, the highest number recorded. On average, 8729
      Nigerians across the 36 states of the federation, and a total of 314,230
      Nigerians nationwide.
    </p>
  </div>

  <div class="text">
    <p>
      Even though the largest economy in Africa still struggles with how to
      involve its citizenry in electoral processes, other African countries have
      recorded a low turnout recently. Tunisia in its just concluded
      parliamentary election recorded a mere 11 percent of voters turnout.
    </p>
  </div>
</main>

<style>
  * {
    box-sizing: border-box;
  }

  p {
    margin: 0px;
  }

  main {
    margin: 0 auto;
    max-width: 700px;
    position: relative;
  }

  .text {
    margin: 0 1rem;
    margin-bottom: 2rem;
    line-height: 1.75;
    font-size: 1.25rem;
    font-family: "Tinos";
    font-weight: 400;
    color: #313131;
  }

  .first-text {
    margin-top: 9rem;
    font-style: italic;
  }

  .sticky {
    position: sticky;
    top: 10%;
    flex: 1 1 60%;
    margin: 0 auto;
    width: 700px;
    text-align: center;
  }

  .section-container {
    margin: 0 0.5rem;
    text-align: center;
    transition: background 100ms;
    display: flex;
    flex-direction: column-reverse;
  }

  .step {
    height: 100vh;
    display: flex;
    place-items: center;
    justify-content: center;
  }

  .step-content {
    font-size: 1.25rem;
    font-family: "Tinos";
    font-weight: 400;
    line-height: 1.75;
    background: rgb(254, 255, 249);
    color: #ccc;
    border-radius: 5px;
    padding: 0.5rem 1.25rem;
    display: flex;
    flex-direction: column;
    justify-content: center;
    transition: background 500ms ease;
    box-shadow: 1px 1px 10px rgba(0, 0, 0, 0.2);
    text-align: left;
    width: 75%;
    margin: 0 auto;
    max-width: 500px;
  }

  .step.active .step-content {
    background: white;
    color: #4e4e4e;
  }

  .steps-container,
  .sticky {
    height: 100%;
  }

  .steps-container {
    flex: 1 1 40%;
    z-index: 10;
  }
  .chart {
    position: relative;
    width: 100%;
    margin: 3rem 0px;
    background-color: #fafafa;
  }

  .chart h4 {
    text-align: center;
    font-size: 1rem;
    font-family: "Lato";
    font-weight: 900;
    color: #141414;
    margin: 0px;
  }
  .flex {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap;
  }

  .chart-main {
    width: 100%;
    margin: 0 auto;
  }

  .wrap {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    margin-bottom: 2rem;
  }

  .wrap p {
    padding-right: 1rem;
    font-size: 1rem;
    font-family: "Lato";
    font-weight: 900;
    color: #141414;
  }

  .wrap .votes {
    color: green;
  }
  /* Comment out the following line to always make it 'text-on-top' */
  @media screen and (max-width: 768px) {
    .section-container {
      flex-direction: column-reverse;
    }
    .sticky {
      width: 95%;
      margin: auto;
    }
  }
</style>

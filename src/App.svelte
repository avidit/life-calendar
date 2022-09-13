<script>
  import Arrow from "./lib/Arrow.svelte";
  import Calendar from "./lib/Calendar.svelte";
  import { DateInput } from "date-picker-svelte";

  let birthday = new Date();
</script>

<main>
  <h1>CALENDAR OF YOUR LIFE</h1>
  <h2>TIME IS LIMITED AND PRECIOUS, HOW DO YOU WANT TO SPEND IT?</h2>
  <div class="weeks">
    <div>WEEKS OF LIFE</div>
    <div class="arrow">
      <Arrow />
    </div>
  </div>

  <div class="date" title="Date of birth">
    <DateInput
      min={new Date(new Date().setFullYear(new Date().getFullYear() - 100))}
      max={new Date()}
      format="yyyy-MM-dd"
      closeOnSelection={true}
      bind:value={birthday}
    />
  </div>

  <div class="years">
    <div class="side">
      <div class="arrow">
        <Arrow />
      </div>
      <div>YEARS OF YOUR LIFE</div>
    </div>
  </div>

  <div class="calendar">
    <Calendar {birthday} />
  </div>

  <div class="stages">
    <div class="side">
      <div>STAGES OF YOUR LIFE</div>
      <div class="arrow">
        <Arrow />
      </div>
    </div>
  </div>
</main>

<style>
  main {
    display: grid;
    grid-template-areas:
      "header header header header header"
      "header2 header2 header2 header2 header2"
      ". weeks . date ."
      "years calendar calendar calendar stages";
  }
  h1 {
    grid-area: header;
    text-align: center;
    font-size: 4em;
    margin: auto;
  }
  h2 {
    grid-area: header2;
    text-align: center;
    font-size: 1em;
    margin-top: auto;
  }
  .weeks {
    grid-area: weeks;
    position: relative;
    left: 30px;
  }
  .date {
    grid-area: date;
    position: relative;
    right: 30px;
  }
  .years {
    grid-area: years;
    position: relative;
    top: 60px;
    left: 60px;
  }
  .stages {
    grid-area: stages;
    position: relative;
    top: 60px;
    right: 40px;
  }
  .calendar {
    grid-area: calendar;
  }
  .side {
    transform: rotate(90deg);
  }
</style>

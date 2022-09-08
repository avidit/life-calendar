<script>
  import Arrow from "./lib/Arrow.svelte";
  import Calendar from "./lib/Calendar.svelte";
</script>

<h1>CALENDAR OF YOUR LIFE</h1>

<main>
  <div class="weeks">
    <div>WEEKS OF LIFE</div>
    <div class="arrow">
      <Arrow />
    </div>
  </div>

  <div class="date">
    <div style="text-align: right">DATE</div>
    <div class="arrow" style="transform: rotate(180deg)">
      <Arrow />
    </div>
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
    <Calendar />
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
      ". weeks . date ."
      "years calendar calendar calendar stages";
    padding: 10px;
  }
  .weeks {
    grid-area: weeks;
  }
  .date {
    grid-area: date;
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
    right: 60px;
  }
  .calendar {
    grid-area: calendar;
  }
  .side {
    transform: rotate(90deg);
  }
</style>

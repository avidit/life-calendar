<script>
    import Circle from "./Circle.svelte";

    const YEARS = 101;
    const WEEKS = 52;
    const MS_PER_WEEK = 604800000; // 1000 * 60 * 60 * 24 * 7;

    export let birthday;

    const getAgeInWeeks = (birthday) => {
        return Math.round(
            (new Date().getTime() - new Date(birthday).getTime()) / MS_PER_WEEK
        );
    };

    const getColorByYear = (year) => {
        if (year <= 12) {
            return "#f87a40";
        } else if (year <= 19) {
            return "#f5aa1f";
        } else if (year <= 34) {
            return "#ff4fe8";
        } else if (year <= 49) {
            return "#F44336";
        } else if (year <= 79) {
            return "#1af041";
        } else {
            return "#2acdf1";
        }
    };
</script>

<div class="container">
    <div class="calendar">
        {#each Array(YEARS) as y, year}
            <div class="year">{year}</div>
            <div class="week">
                {#each Array(WEEKS) as _, week}
                    {@const color = getColorByYear(year)}
                    {@const currentWeek = year * 52 + week}
                    {@const ageInWeeks = getAgeInWeeks(birthday)}
                    <Circle
                        {color}
                        fill={ageInWeeks >= currentWeek}
                        blink={ageInWeeks === currentWeek}
                    />
                {/each}
            </div>
        {/each}
    </div>
    <div class="labels">
        <p class="label-childhood">Childhood (0 - 12)</p>
        <p class="label-adolesence">Adolescence (13 - 19)</p>
        <p class="label-early-adulthood">Early Adulthood (20 - 34)</p>
        <p class="label-middle-adulthood">Middle Adulthood (35 - 49)</p>
        <p class="label-mature-adulthood">Mature Adulthood (50 - 79)</p>
        <p class="label-late-adulthood">Late Adulthood (80 - 100)</p>
    </div>
</div>

<style>
    .container {
        display: grid;
        grid-template-areas: "calendar label";
        grid-template-columns: 810px 20px;
    }
    .calendar {
        grid-area: calendar;
    }
    .year {
        float: left;
        width: 30px;
        text-align: center;
    }
    .week {
        overflow: hidden;
    }
    .labels {
        grid-area: label;
        font-size: small;
    }
    [class*="label-"] {
        writing-mode: vertical-rl;
    }
    .label-childhood {
        position: relative;
        top: 100px;
    }
    .label-adolesence {
        position: relative;
        top: 190px;
    }
    .label-early-adulthood {
        position: relative;
        top: 280px;
    }
    .label-middle-adulthood {
        position: relative;
        top: 450px;
    }
    .label-mature-adulthood {
        position: relative;
        top: 800px;
    }
    .label-late-adulthood {
        position: relative;
        top: 1200px;
    }
</style>

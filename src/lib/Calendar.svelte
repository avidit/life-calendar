<script>
    import Circle from "./Circle.svelte";

    const YEARS = 101;
    const WEEKS = 52;
    const MS_PER_WEEK = 604800000; // 1000 * 60 * 60 * 24 * 7;
    const birthday = "2000-01-01";
    const ageInWeeks = Math.round(
        (new Date().getTime() - new Date(birthday).getTime()) / MS_PER_WEEK
    );

    const getColor = (year) => {
        if (year <= 12) {
            return "#f5aa1f";
        } else if (year <= 19) {
            return "#f87a40";
        } else if (year <= 34) {
            return "#db61b0";
        } else if (year <= 49) {
            return "#ff4fe8";
        } else if (year <= 79) {
            return "#1af041";
        } else {
            return "#2acdf1";
        }
    };

    const isFilled = (year, week) => ageInWeeks >= year * 52 + week;
</script>

{#each Array(YEARS) as _, year}
    <div class="year">{year}</div>
    <div class="week">
        {#each Array(WEEKS) as _, week}
            <Circle color={getColor(year)} isFilled={isFilled(year, week)} />
        {/each}
    </div>
{/each}

<style>
    .year {
        float: left;
        width: 30px;
        text-align: center;
    }
    .week {
        overflow: hidden;
    }
</style>

<script>
    import Circle from "./Circle.svelte";
</script>

{#each Array(101) as _, i}
    <div class="year">{i}</div>
    <div class="week">
        {#each Array(52) as _, j}
            <Circle />
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

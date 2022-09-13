<script>
    let width = 15;
    let height = 15;
    let viewBox = `0 0 ${width} ${height}`;
    export let title;
    export let color;
    export let fill = false;
    export let blink = false;
</script>

<svg {width} {height} {viewBox}>
    <title>{title}</title>
    <circle
        cx={Number(width) / 2}
        cy={Number(height) / 2}
        r={Math.floor(Number(width) / 2)}
        fill={fill ? color + "B3" : "none"}
        stroke={color}
    />
    {#if blink}
        <animate
            attributeName="opacity"
            dur="1.75s"
            values="0;1;0"
            repeatCount="indefinite"
            begin="0.1"
        />
    {/if}
</svg>

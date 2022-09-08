<script>
    let width = 15;
    let height = 15;
    let viewBox = `0 0 ${width} ${height}`;
    export let isFilled = false;
    export let color;
</script>

<svg {width} {height} {viewBox}>
    <circle
        cx={Number(width) / 2}
        cy={Number(height) / 2}
        r={Math.floor(Number(width) / 2)}
        fill={isFilled ? color + "B3" : "none"}
        stroke={color}
    />
</svg>

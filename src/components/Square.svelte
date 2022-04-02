<script>
    export let col;
    export let row;
    export let handleClick;
    export let showCoordinates;
    let colIndex = "abcdefgh".split("").indexOf(col) + 1;
    let light = row % 2 != colIndex % 2;
    let result = null;
</script>

<div
    on:click={() => {
        result = handleClick(col, row);
        setTimeout(() => {
            result = null;
        }, 1000);
    }}
    class="square"
    class:light
>
    {result == true ? "✅" : result == false ? "❌" : ""}
    {#if showCoordinates}
        {col}{row}
    {/if}
</div>

<style>
    .square {
        display: flex;
        justify-content: center;
        align-items: center;
        font-size: 4vmin;
        background-color: rgb(128, 86, 35);
        cursor: pointer;
    }
    .square.light {
        background-color: rgb(230, 217, 124);
    }
    .square:hover {
        filter: brightness(1.3);
    }
</style>

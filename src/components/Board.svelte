<script>
    export let rows;
    export let cols;
    export let handleClick;
    export let showCoordinates;
    import Square from "./Square.svelte";
</script>

<section class="board">
    {#each rows as row}
        <div class="row">
            {#each cols as col}
                <Square {col} {row} {handleClick} {showCoordinates} />
            {/each}
        </div>
    {/each}
</section>

<style>
    .board {
        width: 70vmin;
        height: 70vmin;
        margin: 0 auto;
        display: grid;
        grid-template-rows: repeat(8, 1fr);
        box-shadow: 0px 0px 4px #0008, 0px 0px 15px #000a;
        position: relative;
        border-radius: 6px;
        overflow: hidden;
    }

    .row {
        display: grid;
        grid-template-columns: repeat(8, 1fr);
    }
</style>

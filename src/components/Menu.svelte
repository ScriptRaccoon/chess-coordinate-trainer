<script>
    import { slide } from "svelte/transition";
    export let startGame;
    export let playing;
    export let showCoordinates;
    export let attemptNumber;
    let attemptNumberString = attemptNumber;
    $: attemptNumber =
        parseInt(attemptNumberString) >= 0
            ? parseInt(attemptNumberString)
            : 1;
    import Toggler from "./Toggler.svelte";
    export let color;
</script>

{#if !playing}
    <menu transition:slide>
        <button on:click={startGame}>Start</button>
        <Toggler bind:color />
        <label
            >Show coordinates
            <input type="checkbox" bind:checked={showCoordinates} />
        </label>
        <label>
            Number of attempts
            <input
                type="number"
                bind:value={attemptNumberString}
                min="1"
            />
        </label>
    </menu>
{/if}

<style>
    menu {
        padding: 20px 10px 0px 10px;
        display: flex;
        justify-content: center;
        align-items: center;
        gap: 30px;
        flex-wrap: wrap;
    }
    button {
        font-family: inherit;
        background-color: hsl(223, 64%, 26%);
        color: white;
        padding: 5px 14px;
        border: none;
        outline: none;
        font-size: 20px;
        border-radius: 5px;
        cursor: pointer;
    }

    button:hover,
    button:focus {
        background-color: hsl(223, 64%, 45%);
    }
    input[type="number"] {
        width: 60px;
        text-align: center;
        font-family: inherit;
        color: inherit;
        font-size: 16px;
        padding: 3px 5px;
        border-radius: 4px;
        cursor: pointer;
        outline: none;
        border: 1px solid #555;
    }
</style>

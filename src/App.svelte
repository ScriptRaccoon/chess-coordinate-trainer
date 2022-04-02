<script>
    import Header from "./components/Header.svelte";
    import Board from "./components/Board.svelte";
    import Menu from "./components/Menu.svelte";
    import Overlay from "./components/Overlay.svelte";
    import Feedback from "./components/Feedback.svelte";
    import { randomInteger } from "./utils.js";
    let color = "white";
    $: rows =
        color == "white"
            ? "87654321".split("")
            : "12345678".split("");
    $: cols =
        color == "white"
            ? "abcdefgh".split("")
            : "hgfedcba".split("");
    let coordinate = "";
    let feedback = "";
    let overlayVisible = false;
    let showCoordinates = false;

    let playing = false;

    let attempt = 0;
    let attemptNumber = 10;
    let mistakes = 0;
    let startTime = null;

    function generateCoordinate() {
        if (attempt >= attemptNumber) {
            coordinate = "";
            const currentTime = new Date().getTime();
            const ellapsedTime = currentTime - startTime;
            const displayedTime = (ellapsedTime / 1000).toFixed(1);
            feedback = `${mistakes} mistakes in ${attemptNumber} attempts within ${displayedTime}s`;
            playing = false;
        } else {
            attempt++;
            const i = randomInteger(0, 8);
            const j = randomInteger(0, 8);
            coordinate = cols[i] + rows[j];
            feedback = coordinate;
            overlayVisible = true;
            setTimeout(() => {
                overlayVisible = false;
            }, 1000);
        }
    }

    function startGame() {
        if (playing) return;
        playing = true;
        showCoordinates = false;
        feedback = "";
        attempt = 0;
        mistakes = 0;
        startTime = new Date().getTime();
        feedback = "3";
        setTimeout(() => {
            feedback = "2";
        }, 1000);
        setTimeout(() => {
            feedback = "1";
        }, 2000);
        setTimeout(() => {
            feedback = "";
            generateCoordinate();
        }, 3000);
    }

    function handleClick(col, row) {
        if (!playing) return;
        if (col + row == coordinate) {
            generateCoordinate();
            return true;
        } else {
            mistakes++;
            return false;
        }
    }
</script>

<Header />
<main>
    <Board {rows} {cols} {handleClick} {showCoordinates} />
    <Overlay {coordinate} {overlayVisible} />
</main>
<Menu
    {startGame}
    {playing}
    bind:showCoordinates
    bind:attemptNumber
    bind:color
/>
<Feedback {feedback} />

<style>
    :global(*) {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
    }
    :global(body) {
        font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
        color: #222;
    }
    main {
        position: relative;
    }
</style>

<script>
    export let color = "white";
    let on = color == "white" ? false : true;
    $: color = on ? "black" : "white";
</script>

<div
    title="color"
    class="toggler"
    class:on
    on:click={() => {
        on = !on;
    }}
>
    <div class="ball" />
</div>

<style>
    .toggler {
        --height: 20px;
        --width: 36px;
        width: var(--width);
        height: var(--height);
        position: relative;
        border-radius: 100vw;
        outline: 1px solid #555;
        display: inline-flex;
        cursor: pointer;
    }
    .ball {
        position: absolute;
        border-radius: 50%;
        width: var(--height);
        height: var(--height);
        left: 0px;
        transition: left 180ms ease-out, background 200ms ease-out;
        background: linear-gradient(150deg, white, #bbb);
        outline: 1px solid #555;
    }
    .toggler.on .ball {
        left: calc(var(--width) - var(--height));
        background: linear-gradient(150deg, black, #555);
        outline: 1px solid #000;
    }
</style>

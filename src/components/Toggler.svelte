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
        border: 1px solid #555;
        display: inline-flex;
        cursor: pointer;
        box-sizing: content-box;
    }
    .ball {
        position: absolute;
        border-radius: 50%;
        width: var(--height);
        height: var(--height);
        top: -1px;
        left: 0px;
        transition: left 180ms ease-out, background 200ms ease-out;
        background: linear-gradient(150deg, white, #bbb);
        border: 1px solid #555;
        box-sizing: content-box;
        transform: translateX(-1px);
    }
    .toggler.on .ball {
        left: calc(var(--width) - var(--height));
        background: linear-gradient(150deg, black, #555);
        border: 1px solid #000;
    }
</style>

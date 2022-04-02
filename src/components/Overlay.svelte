<script>
    export let coordinate;
    export let overlayVisible;
</script>

<aside style="opacity: {overlayVisible ? 1 : 0}">
    {coordinate}
</aside>

<style>
    aside {
        position: absolute;
        left: 50%;
        top: 50%;
        transform: translate(-50%, -50%);
        display: flex;
        justify-content: center;
        align-items: center;
        pointer-events: none;
        font-size: 25vmin;
        z-index: 10;
        text-align: center;
        color: white;
        font-family: Arial, Helvetica, sans-serif;
        font-weight: bold;
        text-shadow: 5px 5px 20px #000a;
        transition: opacity 200ms linear;
    }
</style>

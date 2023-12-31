<script lang="ts">
    import Aspiring from "../assets/Aspiring.svelte";
    import Christianity from "../assets/Christianity.svelte";
    import Inquisitive from "../assets/Inquisitive.svelte";
    import Lost from "../assets/Lost.svelte";
    import Paradox from "../assets/Paradox.svelte";
    import Procrastination from "../assets/Procrastination.svelte";

    export let gridSize: number;
    export let maxGraphics: number;
    let grid = Array(gridSize).fill(Array(gridSize).fill(false));

    function getRandomBoolean() {
        return Math.random() < 0.5;
    }

    function generateGrid() {
        let graphicsCount = 0;
        grid = grid.map((row, rowIndex) => row.map((cell: boolean, colIndex: number) => {
            if (graphicsCount < maxGraphics && colIndex !== 2 && colIndex !== 3 && getRandomBoolean()) {
                graphicsCount++;
                return true;
            }
            return false;
        }));
    }

    const minInterval = 5000;
    const maxInterval = 10000;

    function getRandomInterval() {
        return Math.floor(Math.random() * (maxInterval - minInterval + 1)) + minInterval;
    }

    setInterval(generateGrid, getRandomInterval());

    const components = [Aspiring, Christianity, Inquisitive, Lost, Paradox, Procrastination];
    function randomComponent() {
        return components[Math.floor(Math.random() * components.length)];
    }
</script>

<div class="grid" style="--gridSize: {gridSize}">
    {#each grid as row, _}
        {#each row as cell, _}
            <div class="grid-item {cell ? "show" : ""}">
                <svelte:component class="graphic" this={randomComponent()} />
            </div>
        {/each}
    {/each}
</div>

<style>
    .grid {
        z-index: -1;
        position: absolute;
        display: grid;
        grid-template-columns: repeat(var(--gridSize), 1fr);
        grid-template-rows: repeat(var(--gridSize), 1fr);
        grid-auto-rows: 1fr;
        grid-auto-columns: 1fr;
        gap: 10px;
        height: 100vh;
        width: 100vw;
        top: 0;
        left: 0;
        
    }

    .grid-item {
        opacity: 0;
        fill: #2f2f2f;
        stroke: #2f2f2f;
        color: #2f2f2f;
        background-color: transparent;
        width: 100%; /*calc(100% / var(--gridSize));*/
        height: 100%; /*calc(100% / var(--gridSize));*/
        overflow: hidden;
        object-fit: contain;
        transition: 0.5s ease-in-out;
    }
    .show {
        fill: #454ADE;
        stroke: #454ADE;
        color: #454ADE;
        opacity: 1;
        transition: 0.5s ease-in-out;
    }
</style>

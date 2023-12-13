<script lang="ts">
    export let gridSize: number;
    export let maxGraphics: number;
    let grid = Array(gridSize).fill(Array(gridSize).fill(false));

    function getRandomBoolean() {
        return Math.random() < 0.5;
    }

    function generateGrid() {
        let graphicsCount = 0;
        grid = grid.map(row => row.map(() => {
            if (graphicsCount < maxGraphics && getRandomBoolean()) {
                graphicsCount++;
                return true;
            }
            return false;
        }));
    }

    /*function generateGrid() {
        grid = grid.map(row => row.map(() => getRandomBoolean()));
    }*/

    const minInterval = 5000;
    const maxInterval = 10000;

    function getRandomInterval() {
        return Math.floor(Math.random() * (maxInterval - minInterval + 1)) + minInterval;
    }

    setInterval(generateGrid, getRandomInterval());
</script>

<div style="--gridSize: {gridSize}" class="grid">
    {#each grid as row, rowIndex}
        {#each row as cell, cellIndex}
            <div class="graphic" style="background-color: {cell ? "#454ADE" : "transparent"}"></div>
        {/each}
    {/each}
</div>

<style>
    .grid {
        z-index: -999;
        position: absolute;
        display: grid;
        height: 100vh;
        width: 100vw;
        top: 0;
        left: 0;
        grid-template-columns: repeat(var(--gridSize), 1fr);
        grid-template-rows: repeat(var(--gridSize), 1fr);
        gap: 10px;
    }

    .graphic {
        background-color: transparent;
        height: 100%;
        width: 100%;
        transition: 0.5s ease-in-out;
    }
</style>

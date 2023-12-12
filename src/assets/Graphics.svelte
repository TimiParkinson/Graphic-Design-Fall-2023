<script lang="ts">
    import Aspiring from "./Aspiring.svelte";
    import Christianity from "./Christianity.svelte";
    import Inquisitive from "./Inquisitive.svelte";
    import Lost from "./Lost.svelte";
    import Paradox from "./Paradox.svelte";
    import Procrastination from "./Procrastination.svelte";
</script>

<div class="grid">
    <div class="graphic">
        <Aspiring />
        <p>Aspiring</p>
    </div>
    <div class="graphic">
        <Christianity />
        <p>Christianity</p>
    </div>
    <div class="graphic">
        <Inquisitive />
        <p>Inquisitive</p>
    </div>
    <div class="graphic">
        <Lost />
        <p>Lost</p>
    </div>
    <div class="graphic">
        <Paradox />
        <p>Paradox</p>
    </div>
    <div class="graphic">
        <Procrastination />
        <p>Procrastination</p>
    </div>
</div>

<style lang="scss">
    .grid {
        display: grid;
        grid-template-columns: repeat(3, 0.2fr);
        justify-content: center;
        align-items: center;
        width: 40vw;
    }
    .graphic {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        
    }
</style>

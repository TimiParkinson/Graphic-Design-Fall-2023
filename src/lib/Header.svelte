<script lang="ts">
    export let page: string = "voice";
    export let pages: any = {
        home: "Home",
        voice: "Voice",
        identity: "Identity",
        promises: "Promises",
        values: "Values",
        positioning: "Positioning"
    };
</script>

<div>
    {#each Object.keys(pages) as pageName}
        {#if page === pageName}
            <button class="current" on:click={() => page = pageName}>{pageName}</button>
        {:else}
            <button on:click={() => page = pageName}>{pageName}</button>
        {/if}
    {/each}
</div>

<style lang="scss">
    div {
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: space-evenly;
        width: 50vw;
        margin: auto;
        margin-bottom: 1vw;
        top: 0;
        left: 25vw;
    }

    button {
        border: none;
        background: none;
        font-size: 1.5vw;
        text-decoration: none;
        margin-bottom: 0;
        transition: 0.3s ease-in-out;
        &::after {
            content: ""; 
            display: block;
            margin: auto;
            width: 0;
            height: 0.1vh;
            background: transparent;
            transition: 0.3s ease-in-out;
        }
        &:hover {
            color: #00A676;
            &::after {
                width: 100%;
                background: #00A676;
            }
        }
        &.current {
            color: #2f2f2f;
            &:hover {
                color: #454ADE;
                &::after {
                    width: 0%;
                    background: #454ADE;
                }
            }
        }
    }
</style>
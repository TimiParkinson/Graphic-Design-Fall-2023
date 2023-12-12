<script lang="ts">
    export let page: string = "home";

</script>

<div>
    <p on:click={() => page = "home"}>Home</p>
    <p on:click={() => page = "voice"}>Voice</p>
    <p on:click={() => page = "identity"}>Identity</p>
    <p on:click={() => page = "promises"}>Promises</p>
    <p on:click={() => page = "values"}>Values</p>
    <p on:click={() => page = "positioning"}>Positioning</p>
</div>

<style lang="scss">
    div {
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: center;
        width: 100vw;
    }

    p {
        font-size: 1vw;
        margin-bottom: 0;
    }
</style>
<script lang="ts">
    import Graphics from "../assets/Graphics.svelte";

    let sections: any = [
        {
            title: "Target Audience",
            clicked: false,
            content: "<p> This portfolio is targeted toward future educators, employers, coworkers, and clients. </p>"
        },
        
        {
            title: "Graphics",
            clicked: false,

        },

        {
            title: "Name Plate",
            clicked: false,
            content: `<p style="font-size: 4vw;"><span style="font-size: 16vw;">c</span>hristian<span style="font-size: 16vw;">p</span>arkinson</p>`
        },
        
        {
            title: "Slogan",
            clicked: false,
            content: `<p style="font-size: 6vw"> I GOT NOW </p>`
        }
    ];
</script>
<container>
    {#each sections as section}
        <div on:click={() => section.clicked = !section.clicked} class:clicked={section.clicked}>
            <h1>{section.title}</h1>
            {#if section.clicked}
                <content>
                    {#if section.title === "Graphics"}
                        <Graphics />
                    {:else}
                        {@html section.content}
                    {/if}
                </content>
            {/if}
        </div>
    {/each}
</container>

<style lang="scss">
    container {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: space-evenly;
        height: 90vh;
    }
    h1 {
        font-size: 2vw;
        margin-bottom: 0;
    }
    content {
        display: flex;
        justify-content: center;
        align-items: center;
        width: 100%;
        text-align: center;
        font-size: 1.2vw;
    }
    div {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        height: 20vh;
        width: 33vw;
        background-color: #FCFAEE;
        color: #141414;
        border-radius: 0.2vw;
        transition: 0.3s;
        &:hover {
            height: 30vh;
            transition: 0.3s;
            background-color: #00A676;
            color: #FCFAEE;
            &~ div {
                height: 17vh;
                transition: 0.3s;
            }
        }
        &:has(~ div:hover) {
            height: 17vh;
            transition: 0.3s;
        }
        &.clicked {
            z-index: 10000;
            position: absolute;
            width: 50vw;
            height: 80vh;
            background-color: #00A676;
            color: #FCFAEE;
            transition: 0.5s 0.2s;
            &~ div {
                opacity: 0;
                transform: translateY(100vh);
                transition: 0.5s;
            }
        }
        &:has(~ div.clicked) {
            opacity: 0;
            transform: translateY(-100vh);
            transition: 0.5s;
        }
    }
    .svg {
        display: none
    }
</style>
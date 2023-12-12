<script lang="ts">

let sections: any = [
        {
            title: "The Vision",
            clicked: false,
            content: `<p style="font-size: 1.5vw;">To be well-learned in all things.</p>`
        },
        
        {
            title: "The Mission",
            clicked: false,
            content: `<p style="font-size: 1.5vw;">To expand my scope of S.T.E.M. pathways through rigorous coursework, internship opportunities, and personal projects. I am commited to understanding that which I do not.</p>`

        }
    ];

</script>
<container>
    {#each sections as section}
        <div on:click={() => section.clicked = !section.clicked} class={section.title} class:clicked={section.clicked}>
            <h1>{section.title}</h1>
            {#if section.clicked}
                <content>
                    {@html section.content}
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
        border-radius: 0.5vw;
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
    h1 {
        z-index: 1000;
    }
    p {
        font-size: 2vw;
    }
</style>
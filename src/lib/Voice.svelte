<script lang="ts">
    let sections: any = [
        {
            section: "Target Audience",
            clicked: false,
            content: "This is the content for Target Audience"
        },
        
        {
            section: "Graphics",
            clicked: false,
            content: "This is the content for Graphics"
        },
        
        {
            section: "Name Plate",
            clicked: false,
            content: "This is the content for Name Plate"
        },
        
        {
            section: "Slogan",
            clicked: false,
            content: "This is the content for Slogan"
        }
    ];

</script>
<container>
    {#each sections as section}
        <div on:click={() => section.clicked = !section.clicked} class:clicked={section.clicked}>
            <h1>{section.section}</h1>
            {#if section.clicked}
                <content>
                    {section.content}
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
</style>
<script lang="ts">
    import Logo from "../assets/Logo.svelte";

    let sections: any = [
        {
            title: "Color Palette",
            clicked: false,
            content: `<div style="display: flex; justify-content: center; align-items: end; border-radius: 0.2vw; border-style: solid; border-color: #FCFAEE; border-width: 0.05vw; width: 25%; height: 100%; background-color: #141414;"><p>Night</p></div>
                <div style="display: flex; justify-content: center; align-items: end; border-radius: 0.2vw; border-style: solid; border-color: #FCFAEE; border-width: 0.05vw; width: 25%; height: 100%; background-color: #2F2F2F;"><p>Jet</p></div>
                <div style="display: flex; justify-content: center; align-items: end; border-radius: 0.2vw; border-style: solid; border-color: #FCFAEE; border-width: 0.05vw; width: 25%; height: 100%; background-color: #454ADE;"><p>Iris</p></div>
                <div style="display: flex; justify-content: center; align-items: end; border-radius: 0.2vw; border-style: solid; border-color: #FCFAEE; border-width: 0.05vw; width: 25%; height: 100%; background-color: #00A676;"><p>Jade</p></div>`
        },
        
        {
            title: "Logo",
            clicked: false,

        },

        {
            title: "Typography",
            clicked: false,
            content: `<div>
                <h1 style="font-size: 1.5vw;">ABCDEFGHIJKLMNOPQRSTUVWXYZ 1234567890</h1>
                <p>ABCDEFGHIJKLMNOPQRSTUVWXYZ 1234567890</p>
            </div>`
        }
    ];
</script>
<container>
    {#each sections as section}
        <div on:click={() => section.clicked = !section.clicked} class={section.title} class:clicked={section.clicked}>
            <h1>{section.title}</h1>
            {#if section.clicked}
                <content>
                    {#if section.title == "Logo"}
                        <Logo />
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
    .Color.clicked {
        background: none;
    }
    .Color content {
        position: absolute;
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: space-evenly;
        width: 100%;
        height: 100%;
        color: #FCFAEE;
        font-size: 2vw;
        border-radius: 0.2vw;
        border-color: #FCFAEE;
        border-width: 0.2vw;
        div {
            p{
                opacity: 0;
                transition: 0.3s;
            }
            &:hover {
            
                p {
                    opacity: 1;
                    transition: 0.3s;
                }
            }
        }
    }
    h1 {
        z-index: 1000;
    }
    p {
        font-size: 2vw;
    }
</style>
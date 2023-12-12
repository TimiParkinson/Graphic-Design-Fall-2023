<script lang="ts">
    import ValuesPageGraphic from "../assets/Values Page Graphic.svelte";
</script>

<div>
    <ValuesPageGraphic />
    <div>
        <p>Curiosity</p>
        <p>Integrity</p>
        <p>Excellence</p>
        <p>Productivity</p>
    </div>
</div>

<style lang="scss">
    div {
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: center;
        height: 90vh;
        transition: 0.3s;
        div {
            display: none;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 90vh;
            p {
                opacity: 0;
                transform: translate(-100%, 0%);
                font-size: 2vw;
                margin-bottom: 0;
                transition: 0.3s;
            }
        }
        &:hover {
            div {
                display: flex;
                p {
                    opacity: 1;
                    transform: translate(0, 0);
                    transition: 0.3s;
                }
            }
        }
    }
   
</style> 


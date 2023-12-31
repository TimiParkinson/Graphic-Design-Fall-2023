<script lang="ts">
    import ValuesPageGraphic from "../assets/Values Page Graphic.svelte";

    let show: boolean = false;
</script>

<div class="page">
    <ValuesPageGraphic/>
    <div class="p-container" class:show>
        <p>Curiosity</p>
        <p>Integrity</p>
        <p>Excellence</p>
        <p>Productivity</p>
    </div>
</div>

<style lang="scss">
    .page {
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: center;
        height: 90vh;
        &:hover {
            .p-container {
                p {
                    opacity: 1;
                    transform: translate(300%, 0);
                    transition: 0.3s;
                    @for $i from 1 through 4 {
                        &:nth-child(#{$i}) {
                            transition-delay: 0.1s * $i;
                        }
                    }
                }
            }
        }
    }
    .p-container {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        p {
            opacity: 0;
            transform: translate(-100%, 0%);
            font-size: 2vw;
            margin-bottom: 0;
            transition: 0.3s;
            @for $i from 1 through 4 {
                &:nth-child(#{$i}) {
                    transition-delay: 0.05s * $i;
                }
            }
        }
    }
</style> 


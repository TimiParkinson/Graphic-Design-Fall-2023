<script lang="ts">
    import Landing_SVG from "../assets/Landing Page Graphic.svelte";
</script>

<container>
    <div>
        <img src="/Painting.jpg" alt="Christian Parkinson in front of a painting." />
        <img src="/Books.jpg" alt="Christian Parkinson in front of books." />
    </div>
    <p>I stand out because despite the assumptions and stereotypes against me, I don't conform to them. I am often described as that one black dude who doesn't "act black". I am often characterized as that one dude who might be gay. Does that change the fact that I'm black and straight? No.</p>
</container>

<style lang="scss">
    container {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        height: 90vh;
        width: 100vw;
        div {
            display: flex;
            justify-content: space-evenly;
            width: 80%;
            height: 80%;
        }
    }

    p {
        width: 90%;
        font-size: 2vw;
        margin-bottom: 0;
    }

    img {
        position: relative;
        display: block;
        width: 50%;
        object-fit: cover;
        border-radius: 0.2vw;
        transition: 0.3s;
        &:hover {
            width: 75%;
            &::after {
                content: "HELLO WORLD!!!!!!!!!!!!!!!!!!!!!!!!!!!"; /* Use the alt attribute as content for ::before */
                background: rgba(255, 255, 255, 0.8);
                padding: 0.5rem;
                border-radius: 0.2vw;
                transition: opacity 0.3s;
                opacity: 1;
            }
            &~ img {
                width: 25%;
                transition: 0.3s;
            }
        }
        &:has(~ img:hover) {
            width: 25%;
            transition: 0.3s;
        }
    }
</style>
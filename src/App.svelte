<script lang="ts">
  import Header from './lib/Header.svelte';
  import Home from './lib/Home.svelte';
  import Voice from './lib/Voice.svelte';
  import Identity from './lib/Identity.svelte';
  import Promises from './lib/Promises.svelte';
  import Values from './lib/Values.svelte';
  import Positioning from './lib/Positioning.svelte';
  let page = "home";
  let pages = {
    home: Home,
    voice: Voice,
    identity: Identity,
    promises: Promises,
    values: Values,
    positioning: Positioning
  };
</script>
<main>
  <Header bind:page />
  <svelte:component this={pages[page]} />
</main>

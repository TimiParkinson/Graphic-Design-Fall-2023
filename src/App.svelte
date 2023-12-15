<script lang="ts">
  import Header from './lib/Header.svelte';
  import Home from './lib/Home.svelte';
  import Voice from './lib/Voice.svelte';
  import Identity from './lib/Identity.svelte';
  import Promises from './lib/Promises.svelte';
  import Values from './lib/Values.svelte';
  import Positioning from './lib/Positioning.svelte';
  import Background from './lib/Background.svelte';

  // Page Settings \\
  let page: string; //page as const
  let pages: any = {
    home: Home,
    voice: Voice,
    identity: Identity,
    promises: Promises,
    values: Values,
    positioning: Positioning
  };

  // Background Settings \\
  let gridSize: number = 6;
  let maxGraphics: number = 8;
</script>
<main>
  <Header bind:page />
  <svelte:component this={pages[page]} />
  <Background gridSize={gridSize} maxGraphics={maxGraphics}/>
</main>

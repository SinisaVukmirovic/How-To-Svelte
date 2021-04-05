<script>
    import { continents } from './data/continents-data.js';

    import Continent from './components/Continent.svelte';
</script>

<!-- MarkUp -->
<h2>Accordion</h2>

{#each continents as { heading, content, learnurl, mapurl }}
    <Continent {heading} {content} />
{/each}

<style>

</style>
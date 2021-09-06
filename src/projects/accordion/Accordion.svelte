<script>
    import { continents } from './data/continents-data.js';

    import Continent from './components/Continent.svelte';    
    import ModalMap from './components/ModalMap.svelte';

    let modalShowing = false;
    let continentMap = '';

    const showModal = (mapUrl) => {
        continentMap = mapUrl;
        modalShowing = true;
    }
</script>

<!-- MarkUp -->
<section id="accordion">
    <h2>Accordion</h2>

    {#if modalShowing}
        <ModalMap on:click={() => modalShowing = false} mapUrl={continentMap} />
    {/if}

    {#each continents as { heading, content, learnurl, mapurl }}
        <Continent {heading} {content} learnMore={learnurl} on:click={() => showModal(mapurl)} />
    {/each}
</section>

<style>

</style>
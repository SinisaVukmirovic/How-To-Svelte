<script>
	import SearchFilter from './projects/search-filter/SearchFilter.svelte';
	import Autocomplete from './projects/autocomplete/Autocomplete.svelte';
	import SlideshowGallery from './projects/slideshow-gallery/SlideshowGallery.svelte';
	import SidebarMenu from './projects/sidebar-menu/SidebarMenu.svelte';
	import ProgressBar from './projects/progress-bar/ProgressBar.svelte';
	import Lightbox from './projects/lightbox/Lightbox.svelte';
	let lightboxOpen = false;
</script>

<main>
	<h1>How To Svelte</h1>
	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>
	<hr>

	<SearchFilter />

	<Autocomplete />

	<SlideshowGallery />

	<SidebarMenu />

	<ProgressBar />

	<h2>Lightbox</h2>
	<button on:click={() => lightboxOpen = !lightboxOpen}>Lightbox</button>
	{#if lightboxOpen}
		<Lightbox on:click={() => lightboxOpen = !lightboxOpen}/>
	{/if}
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>
<script>
    import HomePage from './components/HomePage.svelte';
    import NewsPage from './components/NewsPage.svelte';
    import ContactPage from './components/ContactPage.svelte';
    import AboutPage from './components/AboutPage.svelte';

    const webpages = [
		{ name: "Home", component: HomePage },
		{ name: "News", component: NewsPage },
		{ name: "Contact", component: ContactPage },
		{ name: "About", component: AboutPage }
	];

    let selectedPage = webpages[0];
	// $: console.dir(selectedPage);

    const loadPage = (obj) => selectedPage = obj;
</script>

<!-- MarkUp -->
<section>
    {#each webpages as webpageObj}
        <button class="tablink" title={webpageObj.name} on:click={() => loadPage(webpageObj)}>{webpageObj.name}</button>
    {/each}

    <svelte:component this={selectedPage.component} />
</section>

<style>
    section {
        margin: 3rem auto;
        padding: 3rem 0;
    }
/* Style tab links */
.tablink {
  background-color: #555;
  color: white;
  float: left;
  border: 1px solid #ccc;
  outline: none;
  cursor: pointer;
  padding: 14px 16px;
  font-size: 17px;
  width: 25%;
}

.tablink:hover {
  background-color: #777;
}
</style>
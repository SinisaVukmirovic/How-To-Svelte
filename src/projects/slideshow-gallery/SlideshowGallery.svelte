<script>
    import { images } from './data/images';

    import Slide from './components/Slide.svelte';
    import { attr } from 'svelte/internal';

    let imageShowIndex = 3;
    $: console.log(imageShowIndex);
</script>

<!-- MarkUp -->
<h2>Slideshow Gallery</h2>
<!-- Container for the image gallery -->
<div class="container">
    {#each images as { id, name, imgUrl, attribution }}
        <Slide image={imgUrl} attr={attribution} alt={name} 
        slideNumber={id + 1} 
        totalSlides={images.lenght} 
        imageShowing={id === imageShowIndex} />
    {/each}
</div>

<style>
/* Position the image container (needed to position the left and right arrows) */
.container {
  position: relative;
}

</style>
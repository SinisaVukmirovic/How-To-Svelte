<script>
    import { images } from './data/images';

    import Slide from './components/Slide.svelte';
    import { attr } from 'svelte/internal';

    import Caption from './components/Caption.svelte';
    import Arrows from './components/Arrows.svelte';

    let imageShowIndex = 3;
    // $: console.log(imageShowIndex);

    const prevSlide = () => {
        if (imageShowIndex === 0) return imageShowIndex = images.length - 1;
        return imageShowIndex -= 1;
    }
    const nextSlide = () => {
        if (imageShowIndex === images.length - 1) return imageShowIndex = 0;
        return imageShowIndex += 1;
    }
</script>

<!-- MarkUp -->
<h2>Slideshow Gallery</h2>
<!-- Container for the image gallery -->
<div class="container">
    {#each images as { id, name, imgUrl, attribution }}
        <Slide image={imgUrl} attr={attribution} alt={name} 
            slideNumber={id + 1} 
            totalSlides={images.length} 
            imageShowing={id === imageShowIndex} 
        />
    {/each}

    <Arrows on:nextSlide={nextSlide} on:prevSlide={prevSlide} />
</div>

<Caption caption={images[imageShowIndex].name}/>

<style>
/* Position the image container (needed to position the left and right arrows) */
.container {
  position: relative;
}

</style>
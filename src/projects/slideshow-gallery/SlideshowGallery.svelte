<script>
    import { images } from './data/images';

    import Slide from './components/Slide.svelte';
    import { attr } from 'svelte/internal';

    import Caption from './components/Caption.svelte';

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
        imageShowing={id === imageShowIndex} />
    {/each}

    <!-- Next and previous buttons -->
    <a href="#prev" class="prev" on:click={prevSlide}>&#10094;</a>
    <a href="#next"  class="next" on:click={nextSlide}>&#10095;</a>

    <Caption caption={images[imageShowIndex].name}/>
</div>

<style>
/* Position the image container (needed to position the left and right arrows) */
.container {
  position: relative;
}

/* Next & previous buttons */
.prev,
.next {
  cursor: pointer;
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  width: auto;
  padding: 16px;
  color: white;
  font-weight: bold;
  font-size: 20px;
  border-radius: 0 3px 3px 0;
  user-select: none;
  -webkit-user-select: none;
}

.prev {
  left: 0;
}
.next {
  right: 0;
}
/* On hover, add a black background color with a little bit see-through */
.prev:hover,
.next:hover {
  background-color: rgba(0, 0, 0, 0.8);
}
</style>
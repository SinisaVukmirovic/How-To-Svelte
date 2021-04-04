<script>
    import { images } from '../slideshow-gallery/data/images';

    import Slide from '../slideshow-gallery/components/Slide.svelte';
    import { attr } from 'svelte/internal';

    import Caption from '../slideshow-gallery/components/Caption.svelte';
    import Arrows from '../slideshow-gallery/components/Arrows.svelte';
    import Thumbnails from '../slideshow-gallery/components/Thumbnails.svelte';

    let imageShowIndex = 3;
    // $: console.log(imageShowIndex);
    $: image = images[imageShowIndex];

    const prevSlide = () => {
        if (imageShowIndex === 0) return imageShowIndex = images.length - 1;
        return imageShowIndex -= 1;
    }
    const nextSlide = () => {
        if (imageShowIndex === images.length - 1) return imageShowIndex = 0;
        return imageShowIndex += 1;
    }

    const showClickedSlide = (idNumb) => {
        imageShowIndex = idNumb;
    }
</script>

<!-- MarkUp -->
<!-- Container for the image gallery -->
<div class="gallery">
    <div class="container">
        <Slide image={image.imgUrl}
            attr={image.attribution}
            alt={image.name} 
            slideNumber={image.id + 1} 
            totalSlides={images.length} 
            imageShowing={image.id === imageShowIndex} 
        />

        <Arrows on:nextSlide={nextSlide} on:prevSlide={prevSlide} />
    </div>

    <Caption caption={image.name} />

    <div class="thumbnails-row">
        {#each images as { id, imgUrl, name }}
            <Thumbnails thumbImg={imgUrl} altTag={name} selected={id === imageShowIndex} 
                on:click={() => showClickedSlide(id)} />
        {/each}
    </div>
</div>

<style>
.gallery {
    width: 70%;
    margin: auto;
}
/* Position the image container (needed to position the left and right arrows) */
.container {
  position: relative;
}

.thumbnails-row {
    display: flex;
    align-items: flex-end;
}
.thumbnails-row:after {
  content: "";
  display: table;
  clear: both;
}

</style>
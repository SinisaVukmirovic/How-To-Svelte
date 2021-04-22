<script>
    import { images } from './data/images';

    import Slide from './components/Slide.svelte';
    import { attr } from 'svelte/internal';

    import Caption from './components/Caption.svelte';
    import Arrows from './components/Arrows.svelte';
    import Thumbnails from './components/Thumbnails.svelte';

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
<section>
    <h2>Slideshow Gallery</h2>
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
</section>

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
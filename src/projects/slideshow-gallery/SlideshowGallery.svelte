<script>
    import Slide from './components/Slide.svelte';

    const images = [
        {
            id: 0,
            name: 'Green Nature',
            imgUrl: 'https://www.w3schools.com/howto/img_woods_wide.jpg',
            attribution: 'svelte.dev'
        }
    ];
</script>

<!-- MarkUp -->
<!-- Container for the image gallery -->
<div class="container">
    <Slide />
</div>

<style>
/* Position the image container (needed to position the left and right arrows) */
.container {
  position: relative;
}

</style>
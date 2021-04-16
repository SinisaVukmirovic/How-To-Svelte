<script>
    import { fade } from 'svelte/transition';

    export let quote;
    export let author;
</script>

<!-- MarkUp -->
<!-- Full-width slides/quotes -->
<div class="mySlides" transition:fade>
    <q>{quote}</q>
    <p class="author">&mdash;{author}</p>
  </div>

<style>
    /* Slides */
.mySlides {
  display: block;
  padding: 80px;
  text-align: center;
}

/* Add an italic font style to all quotes */
q {font-style: italic;}

/* Add a blue color to the author */
.author {color: cornflowerblue;}
</style>
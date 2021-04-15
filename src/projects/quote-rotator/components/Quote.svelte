<script>
    export let quote;
    export let author;
</script>

<!-- MarkUp -->
<!-- Full-width slides/quotes -->
<div class="mySlides">
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

/* Add a blue color to the author */
.author {color: cornflowerblue;}
</style>
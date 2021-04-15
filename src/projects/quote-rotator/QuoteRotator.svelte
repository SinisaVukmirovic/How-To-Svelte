<script>
    import { quotes } from './data/quoteData';

    import Quote from './components/Quote.svelte';

    let quoteIndex = 0;
    $: console.log(quoteIndex);
    $: quote = quotes[quoteIndex].quote;
    $: author = quotes[quoteIndex].author;

    const prevQuote = () => {
        quoteIndex -= 1;
    }

    const nextQuote = () => {
        quoteIndex += 1;
    }
</script>

<!-- MarkUp -->
<h2>Quote Rotator</h2>

<!-- Slideshow container -->
<div class="slideshow-container">
    <Quote {quote} {author} />
  
    <!-- Next/prev buttons -->
    <span class="prev" on:click={prevQuote}>&#10094;</span>
    <span class="next" on:click={nextQuote}>&#10095;</span>
  </div>
  
  <!-- Dots/bullets/indicators -->
  <div class="dot-container">
    <span class="dot" onclick="currentSlide(1)"></span>
    <span class="dot" onclick="currentSlide(2)"></span>
    <span class="dot" onclick="currentSlide(3)"></span>
  </div>

<style>
/* Slideshow container */
.slideshow-container {
  position: relative;
  background: #f1f1f1f1;
}

/* Next & previous buttons */
.prev, .next {
  cursor: pointer;
  position: absolute;
  top: 50%;
  width: auto;
  margin-top: -30px;
  padding: 16px;
  color: #888;
  font-weight: bold;
  font-size: 20px;
  border-radius: 0 3px 3px 0;
  user-select: none;
}

/* Position the "next button" to the right */
.next {
  position: absolute;
  right: 0;
  border-radius: 3px 0 0 3px;
}
.prev {
  position: absolute;
  left: 0;
  border-radius: 3px 0 0 3px;
}

/* On hover, add a black background color with a little bit see-through */
.prev:hover, .next:hover {
  background-color: rgba(0,0,0,0.8);
  color: white;
}

/* The dot/bullet/indicator container */
.dot-container {
  text-align: center;
  padding: 20px;
  background: #ddd;
}

/* The dots/bullets/indicators */
.dot {
  cursor: pointer;
  height: 15px;
  width: 15px;
  margin: 0 2px;
  background-color: #bbb;
  border-radius: 50%;
  display: inline-block;
  transition: background-color 0.6s ease;
}

/* Add a background color to the active dot/circle */
.active, .dot:hover {
  background-color: #717171;
}

/* Add an italic font style to all quotes */
q {font-style: italic;}


</style>
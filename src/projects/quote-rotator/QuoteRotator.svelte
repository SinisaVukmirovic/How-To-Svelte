<script>
    import { quotes } from './data/quoteData';

    import Quote from './components/Quote.svelte';
    import Dot from './components/Dot.svelte';
    import ToggleBtn from './components/ToggleBtn.svelte';

    let quoteIndex = 0;
    $: console.log(quoteIndex);
    $: quote = quotes[quoteIndex].quote;
    $: author = quotes[quoteIndex].author;

    const prevQuote = () => {
      if (quoteIndex === 0) {
        quoteIndex = quotes.length-1;
      } else {
        quoteIndex -= 1;
      }	
    }

    const nextQuote = () => {
      if (quoteIndex === quotes.length-1) {
        quoteIndex = 0;
      } else {
        quoteIndex += 1;
      }	
    }

    let toggleOn = false;
    let autoPlay;
    let autoPlaying = false;

    const handleAutoplay = () => {
      if (toggleOn) {
        autoPlay = setInterval(nextQuote, 3000);
        autoPlaying = true;
      }
      else {
        clearInterval(autoPlay);
        autoPlaying = false;
      }
    }
</script>

<!-- MarkUp -->
<h2>Quote Rotator</h2>

<!-- Slideshow container -->
<div class="slideshow-container">
    {#key quote}
      <Quote {quote} {author} />
    {/key}
  
    <!-- Next/prev buttons -->
    <span class="prev" class:disabled={autoPlaying} on:click={prevQuote}>&#10094;</span>
    <span class="next" class:disabled={autoPlaying} on:click={nextQuote}>&#10095;</span>
  </div>
  
  <!-- Dots/bullets/indicators -->
  <div class="dot-container">
      {#each Array(quotes.length) as _, i}
        <Dot {quoteIndex} {autoPlaying} counter={i} on:click={() => quoteIndex = i} />
      {/each}

      <ToggleBtn bind:toggleOn on:change={handleAutoplay} />
  </div>

<style>
/* Slideshow container */
.slideshow-container {
  position: relative;
  background: #f1f1f1f1;
  width: 90%;
  max-width: 50rem;
  margin: 0 auto;
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
  background: #ddd;
  width: 90%;
  max-width: 50rem;
  margin: 0 auto;
  padding: 20px 0;
  display: flex;
  justify-content: center;
  align-items: center;
}

.disabled {
  pointer-events: none;
}
</style>
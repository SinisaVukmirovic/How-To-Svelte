<script>
    export let quoteIndex;
    export let counter;
    export let autoPlaying;
</script>

<!-- MarkUp -->
<span class="dot" class:active={quoteIndex === counter} 
class:disabled={autoPlaying} on:click></span>

<style>
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

.disabled {
  pointer-events: none;
}
</style>
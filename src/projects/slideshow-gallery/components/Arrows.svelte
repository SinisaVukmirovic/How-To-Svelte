<script>
  import { createEventDispatcher } from 'svelte';

  const dispatch = createEventDispatcher();
</script>

<!-- MarkUp -->
<!-- Next and previous buttons -->
<a href="#prev" class="prev" on:click={() => dispatch('prevSlide')}>&#10094;</a>
<a href="#next"  class="next" on:click={() => dispatch('nextSlide')}>&#10095;</a>

<style>
/* Next & previous buttons */
.prev,
.next {
  text-decoration: none;
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
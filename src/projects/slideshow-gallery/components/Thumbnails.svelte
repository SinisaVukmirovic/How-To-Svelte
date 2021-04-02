<script>
    export let thumbImg;
    export let altTag;
    export let selected;
</script>

<!-- MarkUp -->
<!-- Thumbnail images -->
<div class="thumbnail-container">
    <img class="sample cursor" class:active={selected} src={thumbImg} style="width:100%" alt={altTag} on:click />
</div>

<style>

/* Six columns side by side */
/* .thumbnail-container {
  float: left;
} */

/* Add a transparency effect for thumnbail images */
.sample {
  opacity: 0.6;
}
.sample:hover {
  opacity: 1;
}

.active {
    opacity: 1;
    outline: 5px solid red;
    outline-offset: -5px;
}
</style>
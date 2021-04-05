<script>
    import { fly, fade } from 'svelte/transition';
    export let mapUrl;
</script>

<!-- MarkUp -->
<!-- The Modal -->
<div id="myModal" class="modal" transition:fade>

  <!-- Modal content -->
  <div class="modal-content" in:fly={{ y: -500 }} out:fade>
    <span class="close" on:click>&times;</span>
    <img src={mapUrl} alt="Map" />
  </div>

</div>

<style>
/* The Modal (background) */
.modal {
  position: fixed; /* Stay in place */
  z-index: 1; /* Sit on top */
  left: 0;
  top: 0;
  width: 100%; /* Full width */
  height: 100%; /* Full height */
  overflow: auto; /* Enable scroll if needed */
  background-color: rgb(0,0,0); /* Fallback color */
  background-color: rgba(0,0,0,0.4); /* Black w/ opacity */
}

/* Modal Content/Box */
.modal-content {
  background-color: #fefefe;
  margin: 3% auto; /* 15% from the top and centered */
  padding: 20px;
  border: 1px solid #888;
  width: 50%; /* Could be more or less, depending on screen size */
}

/* The Close Button */
.close {
  color: #aaa;
  float: right;
  font-size: 28px;
  font-weight: bold;
}

.close:hover,
.close:focus {
  color: black;
  text-decoration: none;
  cursor: pointer;
}

img {
    width: 100%;
}
</style>
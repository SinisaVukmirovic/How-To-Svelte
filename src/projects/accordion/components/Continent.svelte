<script>
    export let heading;
    export let content;
    export let learnMore;

    let isOpen = false;
</script>

<!-- MarkUp -->
<button class="accordion" class:active={isOpen} on:click={() => isOpen = !isOpen}>
    {heading} 
    {#if isOpen}
        <span class="icon">&minus;</span>
    {:else}
        <span class="icon">&plus;</span>
    {/if}
</button>
<div class="panel" class:open-panel={isOpen}>
  <p>{content}</p>

  <div class="more-options">
      <button on:click>Map</button>
      <a href={learnMore}>Learn More</a>
  </div>
</div>

<style>
/* Style the buttons that are used to open and close the accordion panel */
.accordion {
    font-size: 20px;
  background-color: #eee;
  border: 1px solid #bbb;
  border-radius: 10px;
  color: #444;
  cursor: pointer;
  padding: 18px;
  width: 75%;
  margin: auto;
  text-align: left;
  outline: none;
  transition: 0.4s;
}

/* Add a background color to the button if it is clicked on (add the .active class with JS), and when you move the mouse over it (hover) */
.active, .accordion:hover {
  background-color: #ccc;
}

.panel {
  width: 70%;
  margin: auto;
  padding: 0 18px;
  background-color: white;
  max-height: 0;
  overflow-y: scroll;
  transition: max-height 0.2s ease-out;
}

.open-panel {
    max-height: 150px;
}

button {
    padding: .5rem 1.5rem;
    cursor: pointer;
}

.accordion .icon {
  font-size: 30px;
  line-height: .75;
  color: #777;
  float: right;
}

.more-options {
    display: flex;
    justify-content: space-evenly;
    align-items: center;
}
</style>
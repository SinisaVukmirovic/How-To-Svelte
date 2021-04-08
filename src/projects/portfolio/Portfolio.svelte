<script>
    import { images } from './data/img-data.js';
    import Buttons from './components/Buttons.svelte';
    import Gallery from './components/Gallery.svelte';

    const categories = ['all', 'strength', 'agility', 'inteligence'];

    let selected = 'all';

    const filterCategory = (e) => {
        selected = e.target.dataset.name;
    }
</script>

<!-- MarkUp -->
<h2>Portfolio gallery</h2>

<Buttons>
    {#each categories as category}
        <button class="btn" class:active={selected === category} data-name={category} 
            on:click={filterCategory}>
            {category.toUpperCase()}
        </button>
    {/each}
</Buttons>

<Gallery>
    {#each images as { name, url, key, desc }}
        {#if selected === 'all'}
            <div class="column {key} show">
                <div class="content">
                    <img src={url} alt={name} style="width:100%">
                    <h4>{name}</h4>
                    <p>{desc}</p>
                </div>
            </div>
        {:else}
            <div class="column {key}" class:show={selected === key}>
                <div class="content">
                    <img src={url} alt={name} style="width:100%">
                    <h4>{name}</h4>
                    <p>{desc}</p>
                </div>
            </div>
        {/if}
    {/each}
</Gallery>


<style>

/* Create three equal columns that floats next to each other */
.column {
  float: left;
  width: 33.33%;
  display: none; /* Hide columns by default */
}



/* Content */
.content {
  background-color: white;
  padding: 10px;
}

/* Style the buttons */
.btn {
  border: none;
  outline: none;
  padding: 12px 16px;
  background-color: white;
  cursor: pointer;
}

/* Add a grey background color on mouse-over */
.btn:hover {
  background-color: #ddd;
}

/* Add a dark background color to the active button */
.btn.active {
  background-color: #666;
   color: white;
}

/* The "show" class is added to the filtered elements */
.show {
display: block;
}
</style>
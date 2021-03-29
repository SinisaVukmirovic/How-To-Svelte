<script>
    import { each } from "svelte/internal";
import MenuItem from "./components/MenuItem.svelte";

    let showMenu = false;
    let inputValue = '';

    const menuItems = ['About', 'Base', 'Blog', 'Contact', 'Custom', 'Support', 'Tools'];
    let filteredItems = [];
    // $:console.log(filteredItems);

    const filterFunction = () => {
        filteredItems = menuItems.filter(item => item.toLowerCase().includes(inputValue.toLowerCase()));
    }
</script>

<style>
    .dropbtn {
    background-color: #4CAF50;
    color: white;
    padding: 16px;
    font-size: 16px;
    border: none;
    cursor: pointer;
    }

    /* Dropdown button on hover & focus */
    .dropbtn:hover, .dropbtn:focus {
    background-color: #3e8e41;
    }

    /* The search field */
    #myInput {
    box-sizing: border-box;
    background-image: url('https://s2.svgbox.net/octicons.svg?ic=search-bold&color=000');
    background-position: 14px 12px;
    background-repeat: no-repeat;
    font-size: 16px;
    padding: 14px 20px 12px 45px;
    border: none;
    border-bottom: 1px solid #ddd;
    }

    /* The search field when it gets focus/clicked on */
    #myInput:focus {outline: 3px solid #ddd;}

    /* The container <div> - needed to position the dropdown content */
    .dropdown {
    position: relative;
    display: inline-block;
    }

    /* Dropdown Content (Hidden by Default) */
    .dropdown-content {
    display: none;
    position: absolute;
    background-color: #f6f6f6;
    min-width: 230px;
    border: 1px solid #ddd;
    z-index: 1;
    }

    /* Show the dropdown menu (use JS to add this class to the .dropdown-content container when the user clicks on the dropdown button) */
    .show {display:block;}
</style>

<!-- MarkUp -->
<h2>Search Filter</h2>

<div class="dropdown">
    <button on:click={() => showMenu = !showMenu} class="dropbtn">Dropdown</button>

    <div id="myDropdown" class="dropdown-content" class:show={showMenu}>
        <input type="text" placeholder="Search.." autocomplete="off" id="myInput" bind:value={inputValue} on:keyup={filterFunction}>

        {#if filteredItems.length > 0}
            {#each filteredItems as item}
                <MenuItem label={item} />
            {/each}
        {:else}
            {#each menuItems as item}
                <MenuItem label={item} />
            {/each}
        {/if}
    </div>
</div>
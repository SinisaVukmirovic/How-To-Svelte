<script>
    import { each } from "svelte/internal";
    import MenuItem from "./components/MenuItem.svelte";
    import Button from "./components/Button.svelte";
    import Input from "./components/Input.svelte";

    let showMenu = false;
    let inputValue = '';

    const menuItems = ['About', 'Base', 'Blog', 'Contact', 'Custom', 'Support', 'Tools'];
    let filteredItems = [];
    // $:console.log(filteredItems);

    const filterFunction = () => {
        filteredItems = menuItems.filter(item => item.toLowerCase().includes(inputValue.toLowerCase()));
    }
</script>

<!-- MarkUp -->
<section id="filter">
    <h2>Search Filter</h2>

    <div class="dropdown">
        <Button on:click={() => showMenu = !showMenu} {showMenu} />

        <div id="myDropdown" class="dropdown-content" class:show={showMenu}>
            <Input bind:inputValue on:keyup={filterFunction} />
            <!-- menu -->
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
</section>

<style>
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

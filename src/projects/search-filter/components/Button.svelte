<script>
    export let showMenu;
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
</style>

<!-- MarkUp -->
<button on:click class="dropbtn">{showMenu ? "Hide Menu" : "Show Menu"}</button>

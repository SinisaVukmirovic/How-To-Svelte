<script>
    export let countryName;
</script>

<!-- MarkUp -->
<li class="autocomplete-item" on:click>{countryName}</li>

<style>
    .autocomplete-item {
    text-align: left;
    padding: 10px 20px;
    cursor: pointer;
    background-color: #fff;
    border-bottom: 1px solid #d4d4d4;
    }
    .autocomplete-item:hover {
    /*when hovering an item:*/
    background-color: #e9e9e9;
    }
    .autocomplete-item:active {
    /*when navigating through the items using the arrow keys:*/
    background-color: DodgerBlue !important;
    color: #ffffff;
    }
</style>
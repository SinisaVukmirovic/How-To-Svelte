<script>
    export let inputValue;
</script>

<style>
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
</style>

<!-- MarkUp -->
<input type="text" placeholder="Search.." autocomplete="off" id="myInput" 
bind:value={inputValue} on:keyup>
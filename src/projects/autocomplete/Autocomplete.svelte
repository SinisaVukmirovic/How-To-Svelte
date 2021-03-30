<script>
    import countriesData from './store-data/countries-store.js';

    import Country from './components/Country.svelte';

    let countries;
    // when we use store in svelte, we need to subscribe to it, before we can use it
    countriesData.subscribe(items => countries = items);

    let inputValue = '';

    let filteredCountries = [];
    
    const filterCountries = () => {
        filteredCountries = countries.filter(country => country.startsWith(inputValue));
    }
</script>

<!-- MarkUp -->
<h2>Autocomplete</h2>
<!--Make sure the form has the autocomplete function switched off:-->
<form autocomplete="off">
    <div class="autocomplete" style="width:300px;">
        <input id="myInput" type="text" name="myCountry" bind:value={inputValue} placeholder="Country.." on:input={filterCountries}>

        <ul class="autocomplete-items-container">
            {#each filteredCountries as country}
                <Country countryName={country} />
            {/each}
        </ul>
    </div>
    <input type="submit">

</form>

<style>
    .autocomplete {
    /*the container must be positioned relative:*/
    position: relative;
    display: inline-block;
    }
    input {
    border: 1px solid transparent;
    background-color: #f1f1f1;
    padding: 10px;
    font-size: 16px;
    }
    input[type=text] {
    background-color: #f1f1f1;
    width: 100%;
    }
    input[type=submit] {
    background-color: DodgerBlue;
    color: #fff;
    }
    .autocomplete-items-container {
    position: absolute;
    list-style-type: none;
    border: 1px solid #d4d4d4;
    border-bottom: none;
    border-top: none;
    z-index: 99;
    padding: 0;
    /*position the autocomplete items to be the same width as the container:*/
    top: 100%;
    left: 0;
    right: 0;
    }    
</style>
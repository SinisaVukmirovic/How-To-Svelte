<script>
    import countriesData from './store-data/countries-store.js';

    import Country from './components/Country.svelte';

    let countries;
    // when we use store in svelte, we need to subscribe to it, before we can use it
    countriesData.subscribe(items => countries = items);

    let filteredCountries = [];

    let inputValue = '';
    $: if (!inputValue) {
        filteredCountries = [];
    }
    
    const filterCountries = () => {
        let storageArr = [];
        if (inputValue) {
            filteredCountries = countries.forEach(country => {
                if (country.toLowerCase().startsWith(inputValue.toLowerCase())) {
                    storageArr = [...storageArr, makeMatchBold(country)];
                }
            });
        }
        filteredCountries = storageArr;
    }

    const makeMatchBold = (str) => {
        let matched = str.substring(0, inputValue.length);
        let makeBold = `<strong>${matched}</strong>`;
        let boldedMatch = str.replace(matched, makeBold);
        return boldedMatch;
    }

    const removeBold = (str) => {
        return str.replace(/<(.)*?>/g, '');
    }

    const setInputValue = (country) => {
        inputValue = removeBold(country);
    }

    const submitValue = () => {
        if (inputValue) {
            console.log(`${inputValue} is submitted!`);
            inputValue = '';
        } else {
            alert('You forgot to choose a country!');
        }
    }

    let highlightIndex = null;

    $: highlighterCountry = filteredCountries[highlightIndex];

    const navigateList = (e) => {
        if (e.key === 'ArrowDown' && highlightIndex < filteredCountries.length - 1) {
            highlightIndex === null ? highlightIndex = 0 : highlightIndex += 1;
        } else if (e.key === 'ArrowUp' && highlightIndex !== null) {
            highlightIndex === 0 ? highlightIndex = filteredCountries.length - 1 : highlightIndex -= 1;
        } else if (e.key === 'Enter') {
            setInputValue(highlighterCountry);
        } else {
            return;
        }
    }

</script>

<!-- MarkUp -->
<svelte:window on:keydown={navigateList} />

<h2>Autocomplete</h2>
<!--Make sure the form has the autocomplete function switched off:-->
<form autocomplete="off" on:submit|preventDefault={submitValue}>
    <div class="autocomplete" style="width:300px;">
        <input id="myInputAutocomplete" type="text" name="myCountry" bind:value={inputValue} placeholder="Country.." on:input={filterCountries}>

        <ul class="autocomplete-items-container">
            {#each filteredCountries as country, i}
                <Country countryName={country} highlighted={i === highlightIndex} on:click={() => setInputValue(country)} />
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
    /* top: 2rem; */
    top: 50%;
    left: 0;
    right: 0;
    }    
</style>
<script>
    import { onMount } from 'svelte';

    let phrase = 'React is NOT reactive! React is a terrible name for React.js. As engineers we should be offended by the way React is engeenered to work!';
    let typedCharacters = '';
    let index = 0;
    let typewritter;

    const typeChar = () => {
        if (index < phrase.length) {
            typedCharacters += phrase[index];
            index += 1;
        } else {
            clearInterval(typewritter);
        }
    }

    const typing = () => typewritter = setInterval(typeChar, 150);

    onMount(() => typing());

    // example with typing out the text from input
    let inputPhrase;
    let inputTextCharacters = '';
    let indexForInput = 0;
    let inputTypewritter;

    const typeInputText = () => {
        if (indexForInput < inputPhrase.length) {
            inputTextCharacters += inputPhrase[indexForInput];
            indexForInput += 1;
        } else {
            clearInterval(inputTypewritter);
        }
    }

    const typingOfInput = () => inputTypewritter = setInterval(typeInputText, 150);

</script>

<link href="https://fonts.googleapis.com/css2?family=Special+Elite&display=swap" rel="stylesheet">
<!-- MarkUp -->
<h2>Typewritter Effect</h2>

<h3>{typedCharacters}</h3>

<form on:submit|preventDefault={typingOfInput}>
    <input type="text" placeholder="Type out what you want.." bind:value={inputPhrase} />
    <button>Start</button>
</form>

<h3>{typedCharacters}</h3>

<style>
@import url('https://fonts.googleapis.com/css2?family=Special+Elite&display=swap');
    h3 {
        font-family: 'Special Elite', cursive;
        width: 70%;
        margin: 2rem auto;
        text-align: left;
        line-height: 1.5;
        letter-spacing: 2px;
    }
</style>
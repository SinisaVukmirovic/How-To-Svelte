<script>
    import { onMount } from 'svelte';

    let phrase = 'React is NOT reactive! React is a terrible name for React.js. As engineers we should be offended by the way React is engeenered to work!';
    let typedCharacterss = '';
    let index = 0;
    let typewritter;

    const typeChar = () => {
        if (index < phrase.length) {
            typedCharacterss += phrase[index];
            index += 1;
        } else {
            clearInterval(typewritter);
        }
    }

    const typing = () => typewritter = setInterval( typeChar, 200);

    onMount(() => typing());
</script>

<!-- MarkUp -->
<h2>Typewritter Effect</h2>

<h3>{typedCharacterss}</h3>
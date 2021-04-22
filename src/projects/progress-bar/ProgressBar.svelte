<script>
    import { fly } from 'svelte/transition';
    
    let barWidth = 0;
    let progress;
    let isActive;

    $: if (barWidth === 100) {
        clearInterval(progress);
        isActive = false;
        document.querySelector('#myFile').value = '';
        setTimeout(() => {
            resetProgress();
        }, 3000);
    }

    const addWidth = () => barWidth += 1;

    const resetProgress = () => {
        barWidth = 0;
        clearInterval(progress);
    }

    const makeProgress = () => {
        if (!document.querySelector('#myFile').value) {
            alert('Please, choose a file!');
        } else {
            isActive = true;
            progress = setInterval(addWidth, 20);
        }
    }
</script>

<!-- MarkUp -->
<section>
    <h2>Progress Bar</h2>

    <div class="msg-container">
        {#if barWidth === 100}
        <h3 id="completedMsg" in:fly={{ x: -300}} out:fly={{ x: 300}}>Your file has been uploaded!</h3>
        {/if}
    </div>

    <div id="myProgress">
        <span>{barWidth}%</span>
        <div id="myBar" style="width: {barWidth}%"></div>
    </div>

    <form on:submit|preventDefault={makeProgress}>
        <input type="file" id="myFile" name="filename">
        <button disabled={isActive}>Upload File</button>
        <button on:click|preventDefault={resetProgress}>Cancel</button>
    </form>
</section>


<style>
    .msg-container {
        text-align: center;
        height: 3rem;
        overflow: hidden;
    }

    #completedMsg {
        color: coral;
        animation: blink .75s ease-in-out 3;
    }

    @keyframes blink {
        to {opacity: 0;}
    }

#myProgress {
  width: 100%;
  background-color: #ccc;
  position: relative;
}

#myBar {
  width: 0%;
  height: 30px;
  background-color: coral;
}

span {
    position: absolute;
    font-size: 1.25rem;
    font-weight: bold;
}

form {
    margin: 1rem auto;
}
button {
    cursor: pointer;
}
</style>
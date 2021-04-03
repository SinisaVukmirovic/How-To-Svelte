<script>
    let barWidth = 0;
    let progress;
    let isActive;

    $: if (barWidth === 100) {
        clearInterval(progress);
        isActive = false;
    }

    const addWidth = () => barWidth += 1;

    const makeProgress = () => {
        if (!document.querySelector('#myFile').value) {
            alert('Please, choose a file!');
        } else {
            isActive = true;
            progress = setInterval(addWidth, 10);
        }
    }
</script>

<!-- MarkUp -->
<h2>Progress Bar</h2>

<div id="myProgress">
    <span>{barWidth}%</span>
    <div id="myBar" style="width: {barWidth}%"></div>
</div>

<form on:submit|preventDefault={makeProgress}>
    <input type="file" id="myFile" name="filename">
    <button disabled={isActive}>Upload File</button>
</form>


<style>
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
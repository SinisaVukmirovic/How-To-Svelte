<script>
    import { tweened } from 'svelte/motion';
    import { backInOut } from 'svelte/easing';

    export let framework;
    export let percent;
    export let color;
    export let delay;

    const progress = tweened(15, {
        delay: delay,
        duration: 2000,
        easing: backInOut
    });

    progress.set(percent);
</script>

<!-- MarkUp -->
<div class="container">
    <span class="framework">{framework}</span>
    <div class="skills" style="width: {$progress}%; background-color: {color}">{percent}%</div>
</div>

<style>
/* Container for skill bars */
.container {
  width: 100%; /* Full width */
  background-color: #ddd; /* Grey background */
  border: 1px solid #222;
  border-radius: .5rem;
  margin: 1rem 0;
  position: relative;
}

.framework {
		position: absolute;
		top: 26%;
		left: 15px;
		font-weight: 500;
		color: #000;
	}

.skills {
  text-align: right; /* Right-align text */
  padding-top: 10px; /* Add top padding */
  padding-bottom: 10px; /* Add bottom padding */
  color: white; /* White text color */
  font-weight: bold;
  text-align: center;
}

</style>
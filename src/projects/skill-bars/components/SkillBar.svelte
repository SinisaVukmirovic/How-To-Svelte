<script>
    export let framework;
    export let percent;
    export let color;
</script>

<!-- MarkUp -->
<p>{framework}</p>
<div class="container">
  <div class="skills" style="width: {percent}%; background-color: {color}">{percent}</div>
</div>

<style>
/* Container for skill bars */
.container {
  width: 100%; /* Full width */
  background-color: #ddd; /* Grey background */
  border: 2px solid #222;
  border-radius: .5rem;
}

.skills {
  text-align: right; /* Right-align text */
  padding-top: 10px; /* Add top padding */
  padding-bottom: 10px; /* Add bottom padding */
  color: white; /* White text color */
}

</style>
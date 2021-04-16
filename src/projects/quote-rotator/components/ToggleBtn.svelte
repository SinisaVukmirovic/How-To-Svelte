<script>
    export let toggleOn;
</script>

<!-- MarkUp -->
<!-- Rounded switch -->
<div class="toggle">
    <label class="switch">
        <input type="checkbox" bind:checked={toggleOn} on:change>
        <span class="slider round"></span>
    </label>
</div>

<style>
    .toggle {
		position: relative;
        margin-left: 3rem;
    }
    .toggle:hover::after {
		content: "Auto-play";
		width: 100px;
		position: absolute;
		left: 0;
		top: -30px;
		background-color: white;
		box-shadow: 0 0 3px black;
		padding: 5px 0;
		border-radius: 5px;
    }
/* The switch - the box around the slider */
.switch {
  position: relative;
  display: inline-block;
  width: 60px;
  height: 34px;
}

/* Hide default HTML checkbox */
.switch input {
  opacity: 0;
  width: 0;
  height: 0;
}

/* The slider */
.slider {
  position: absolute;
  cursor: pointer;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: red;
  -webkit-transition: .4s;
  transition: .4s;
}

.slider:before {
  position: absolute;
  content: "";
  height: 26px;
  width: 26px;
  left: 4px;
  bottom: 4px;
  background-color: white;
  -webkit-transition: .4s;
  transition: .4s;
}

input:checked + .slider {
  background-color: #2196F3;
}

input:focus + .slider {
  box-shadow: 0 0 1px #2196F3;
}

input:checked + .slider:before {
  -webkit-transform: translateX(26px);
  -ms-transform: translateX(26px);
  transform: translateX(26px);
}

/* Rounded sliders */
.slider.round {
  border-radius: 34px;
}

.slider.round:before {
  border-radius: 50%;
}
</style>
<script>
    export let avatar;
    export let hero;
    export let flipCard;
    export let details;
</script>

<!-- MarkUp -->
<div class="flip-box-front">
    <h4>{hero}</h4>
    <img src={avatar} alt="Hero Avatar">
  </div>

  <div class="flip-box-back" class:conceal-answer={flipCard}>
        {#each details as detail}
            <p>{detail}</p>
        {/each}
  </div>

<style>
    /* Position the front and back side */
.flip-box-front, .flip-box-back {
  position: absolute;
  width: 100%;
  height: 100%;
  -webkit-backface-visibility: hidden; /* Safari */
  backface-visibility: hidden;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

/* Style the front side */
.flip-box-front {
  background-color: #bbb;
  color: black;
}

@keyframes revealTextSlowly {
		to { color: white }
	}
	
	.conceal-answer {
		animation: revealTextSlowly .3s forwards;
	}

/* Style the back side */
.flip-box-back {
  background-color: dodgerblue;
  /* color: white; */
  color: transparent;
  transform: rotateY(180deg);
}
</style>
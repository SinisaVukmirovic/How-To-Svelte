<script>
    import { cards } from './data/cards-data';

    import Card from './components/Card.svelte';

    let flipCard = false;

    let flipCardIndex = 0;

    $: hero = cards[flipCardIndex].hero;
    $: avatar = cards[flipCardIndex].avatar;
    $: details = cards[flipCardIndex].details;

    const toggleFlipCard = () => flipCard = !flipCard;

    const prevCard = () => {
		flipCard = false;
		if (flipCardIndex === 0) {
			flipCardIndex = cards.length - 1;
		} else {
			flipCardIndex -= 1;
		}
	}
	
	const nextCard = () => {
		flipCard = false;
		if (flipCardIndex === cards.length - 1) {
			flipCardIndex = 0;
		} else {
			flipCardIndex += 1;
		}	
	}
</script>

<!-- MarkUp -->
<section>
  <h2>Flip Card</h2>

  <div class="flip-box">
      <div class="flip-box-inner" class:flipCard={flipCard}>

        <Card {avatar} {hero} {flipCard} {details} />
        
      </div>
  </div>

  <div class="btn-container">
      <button class="arrow-btn" on:click={prevCard}>&#8592;</button>
      <button on:click={toggleFlipCard}>{flipCard ? 'Hide Details' : 'Show Details'}</button>
      <button class="arrow-btn" on:click={nextCard}>&#8594;</button>
  </div>
</section>

<style>
.flip-box {
    margin: 2rem auto;
  background-color: transparent;
  width: 350px;
  height: 250px;
  border: 1px solid #f1f1f1;
  perspective: 1000px; /* Remove this if you don't want the 3D effect */
}

/* This container is needed to position the front and back side */
.flip-box-inner {
  position: relative;
  width: 100%;
  height: 100%;
  text-align: center;
  transition: transform 0.8s;
  transform-style: preserve-3d;
}

/* Do an horizontal flip when you move the mouse over the flip box container */
.flipCard {
  transform: rotateY(180deg);
}


</style>
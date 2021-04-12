<script>
    import { cards } from './data/cards-data';

    let flipCard = false;

    let flipCardIndex = 0;

    $: hero = cards[flipCardIndex].hero;
    $: avatar = cards[flipCardIndex].avatar;
    $: details = cards[flipCardIndex].details;

    const toggleFlipCard = () => flipCard = !flipCard;
</script>

<!-- MarkUp -->
<h2>Flip Card</h2>

<div class="flip-box">
    <div class="flip-box-inner" class:flipCard={flipCard}>

      <div class="flip-box-front">
        <h4>{hero}</h4>
        <img src={avatar} alt="Hero Avatar">
      </div>

      <div class="flip-box-back">
            {#each details as detail}
                <p>{detail}</p>
            {/each}
      </div>
    </div>
</div>

<div class="btn-container">
    <button on:click={toggleFlipCard}>{flipCard ? 'Hide Details' : 'Show Details'}</button>
</div>

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

/* Style the back side */
.flip-box-back {
  background-color: dodgerblue;
  color: white;
  transform: rotateY(180deg);
}
</style>
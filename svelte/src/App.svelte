<script>
	let flipped = false;
</script>

<div class="container">
	<h1 class="title">Flip the card</h1>
	<p class="description">Click the card to see the magic!</p>
	<button
		class="card"
		class:flipped={flipped}
		on:click={() => flipped = !flipped}
	>
		<div class="front">
			<span class="symbol">♠</span>
		</div>
		<div class="back">
			<div class="pattern"></div>
		</div>
	</button>
</div>

<style>
  	@keyframes fadeIn {
		0% { opacity: 0; transform: translateY(-10px); }
		100% { opacity: 1; transform: translateY(0); }
	}

	@keyframes bounce {
		0%, 100% { transform: translateY(0); }
		50% { transform: translateY(-20px); }
	}
  .title {
		font-size: 2em;
		color: var(--fg-1);
		animation: fadeIn 1s ease-in-out;
	}

	.description {
		font-size: 1.2em;
		color: var(--fg-2);
		animation: fadeIn 1.5s ease-in-out;
	}

	.container {
		display: flex;
		flex-direction: column;
		gap: 1em;
		height: 100%;
		align-items: center;
		justify-content: center;
		perspective: 100vh;
	}

	.card {
		position: relative;
		aspect-ratio: 2.5 / 3.5;
		font-size: min(1vh, 0.25rem);
		height: 80em;
		background: var(--bg-1);
		border-radius: 2em;
		transform: rotateY(180deg);
		transition: transform 0.4s;
		transform-style: preserve-3d;
		padding: 0;
    border: 1px solid black;
		user-select: none;
		cursor: pointer;
	}

  .card:hover {
		box-shadow: 0 15px 30px rgba(0, 0, 0, 0.2);
    scale: 1.1;
	}

	.card.flipped {
		transform: rotateY(0);
	}

	.front, .back {
		display: flex;
		align-items: center;
		justify-content: center;
		position: absolute;
		width: 100%;
		height: 100%;
		left: 0;
		top: 0;
		backface-visibility: hidden;
		border-radius: 2em;
		border: 1px solid var(--fg-2);
		box-sizing: border-box;
		padding: 2em;
	}

	.front {
		background: url(./svelte-logo.svg) no-repeat 5em 5em, url(./svelte-logo.svg) no-repeat calc(100% - 5em) calc(100% - 5em);
		background-size: 8em 8em, 8em 8em;
	}

	.back {
		transform: rotateY(180deg);
	}

	.symbol {
		font-size: 30em;
		color: var(--fg-1);
	}

	.pattern {
		width: 100%;
		height: 100%;
		background-color: var(--bg-2);
		/* pattern from https://projects.verou.me/css3patterns/#marrakesh */
		background-image:
		radial-gradient(var(--bg-3) 0.9em, transparent 1em),
		repeating-radial-gradient(var(--bg-3) 0, var(--bg-3) 0.4em, transparent 0.5em, transparent 2em, var(--bg-3) 2.1em, var(--bg-3) 2.5em, transparent 2.6em, transparent 5em);
		background-size: 3em 3em, 9em 9em;
		background-position: 0 0;
		border-radius: 1em;
	}
</style>

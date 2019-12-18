<script>
	let random = getRandNumber();
	let result = "-";
	let guess = 0;
	let guesses = 0;
	
	function submitGuess() {
		if(guess < random) result = 'HIGHER';
		if(guess > random) result = 'LOWER';
		if(guess === random) {
			result = 'CORRECT';
			alert(`CORRECT, NUMBER WAS ${random}. YOU TOOK ${guesses} GUESSES`)
		}
		guesses++;
	
		if(guesses >= 5) {
			result = 'GAME OVER!';
			alert(`GAME OVER, NUMBER WAS ${random}`)
		}
	}
	
	function resetGame() {
		guesses = 0;
		guess = 0;
		result = "-";
		random = getRandNumber();
	}
	
	function getRandNumber() {
		return Math.floor(Math.random() * 11);
	}
</script>

<p>{result}</p>
<input bind:value={guess} type="number">
<button on:click={submitGuess}>Submit Guess</button>
<h1>Guesses: {guesses}</h1>

{#if guesses >= 5 || result === 'CORRECT'}
<button on:click={resetGame}>Reset Game</button>
{/if}

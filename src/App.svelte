<script lang="ts">
	let flipped = $state(false);

	if (location && location.href) {
		var params = location.href.split("?")[1]?.split("&");
		let data: { [key: string]: string } = {};
		for (let x in params) {
			data[params[x].split("=")[0]] = params[x].split("=")[1];
		}

		var html = document.documentElement;
		switch(data["theme"]) {
			case ("light"): {
				html.classList.add("light");
				html.classList.remove("dark");
				break;
			}

			case ("dark"): {
				html.classList.add("dark");
				html.classList.remove("light");
				break;
			}

			default: break;
		}
	}
</script>

<div class="container">
	<button
		class="card {flipped ? 'flipped' : ''}"
		onclick={() => (flipped = !flipped)}
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
	:root {
		--bg-1: hsl(0, 0%, 18%);
		--bg-2: hsl(0, 0%, 30%);
		--bg-3: hsl(0, 0%, 40%);
		--fg-1: hsl(0, 0%, 90%);
		--fg-2: hsl(0, 0%, 70%);
		--fg-3: hsl(0, 0%, 60%);
		--link: hsl(206, 96%, 72%);
		--link-hover: hsl(206, 96%, 78%);
		--link-active: hsl(206, 96%, 64%);
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
		background: var(--fg-3);
		border-radius: 2em;
		transform: rotateY(180deg) rotateZ(3deg) rotateX(-2deg);
		transition:
			transform 750ms
				linear(
					0,
					0.176 4.2%,
					0.333 8.5%,
					0.474 12.9%,
					0.596 17.4%,
					0.704 22.1%,
					0.752 24.5%,
					0.795 26.9%,
					0.835 29.4%,
					0.87 31.9%,
					0.902 34.5%,
					0.93 37.1%,
					0.953 39.5%,
					0.972 41.9%,
					0.989 44.4%,
					1.002 46.9%,
					1.014 49.5%,
					1.023 52.2%,
					1.03 55%,
					1.035 58%,
					1.037 62.6%,
					1.035 67.8%,
					1.029 73.1%,
					1.006 89.3%,
					1.001 94.7%,
					1
				),
			box-shadow 750ms
				linear(
					0,
					0.176 4.2%,
					0.333 8.5%,
					0.474 12.9%,
					0.596 17.4%,
					0.704 22.1%,
					0.752 24.5%,
					0.795 26.9%,
					0.835 29.4%,
					0.87 31.9%,
					0.902 34.5%,
					0.93 37.1%,
					0.953 39.5%,
					0.972 41.9%,
					0.989 44.4%,
					1.002 46.9%,
					1.014 49.5%,
					1.023 52.2%,
					1.03 55%,
					1.035 58%,
					1.037 62.6%,
					1.035 67.8%,
					1.029 73.1%,
					1.006 89.3%,
					1.001 94.7%,
					1
				);
		transform-style: preserve-3d;
		padding: 0;
		user-select: none;
		cursor: pointer;
		box-shadow: -1em 1.5em 5em rgba(0, 0, 0, 0.5);
	}

	.card.flipped {
		box-shadow: 1em 1.5em 5em rgba(0, 0, 0, 0.5);
		transform: rotateY(0);
	}

	.card:not(.flipped):hover {
		transform: rotateY(170deg) rotateZ(4deg) rotateX(-1deg);
	}

	.front,
	.back {
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
		background:
			url(./assets/ek.svg) no-repeat 5em 5em,
			url(./assets/ek.svg) no-repeat calc(100% - 5em) calc(100% - 5em);
		background-size:
			8em 8em,
			8em 8em;
		background-color: var(--fg-1);
		padding-bottom: 10em;
	}

	.back {
		transform: rotateY(180deg);
	}

	.symbol {
		font-size: 30em;
		color: var(--bg-1);
	}

	.pattern {
		width: 100%;
		height: 100%;
		background-color: var(--fg-3);
		/* pattern from https://projects.verou.me/css3patterns/#marrakesh */
		background-image: radial-gradient(var(--fg-1) 0.9em, transparent 1em),
			repeating-radial-gradient(
				var(--fg-1) 0,
				var(--fg-1) 0.4em,
				transparent 0.5em,
				transparent 2em,
				var(--fg-1) 2.1em,
				var(--fg-1) 2.5em,
				transparent 2.6em,
				transparent 5em
			);
		background-size:
			3em 3em,
			9em 9em;
		background-position: 0 0;
		border-radius: 1em;
	}
</style>

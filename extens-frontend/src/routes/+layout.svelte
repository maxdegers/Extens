<script>
	import Header from "./Header.svelte";
	import "./styles.css";
	import {page,image} from "../stores/swipe"

	let xStart = null;
	function touchStart(e) {
		xStart = e.touches[0].clientX;
	}

	function touchMove(e) {
		if (!xStart) return;

		let xEnd = e.touches[0].clientX;
		let diff = xStart - xEnd;

		if (Math.abs(diff) > 100) {
			// you can adjust this value
			if (diff > 0) {
				// swipe left
				console.log("You swiped left");
				if ($page > 0) {
					$page--;
				}
			} else {
				// swipe right
				console.log("You swiped right");
				if ($page < $image.length - 1) {
					$page++;
				}
			}

			xStart = null; // reset for next swipe
		}
	}
</script>

<div class="app" on:touchstart={touchStart} on:touchmove={touchMove}>
	<Header />

	<main>
		<slot />
	</main>

	<footer>
		<p>
			Visit <a
				href="https://github.com/maxdegers?tab=overview&from=2023-04-01&to=2023-04-30"
				>github.com</a
			> to read my profile
		</p>
	</footer>
</div>

<style>
	.app {
		display: flex;
		flex-direction: column;
		min-height: 100vh;
	}

	main {
		flex: 1;
		display: flex;
		flex-direction: column;
		padding: 1rem;
		width: 100%;
		max-width: 90vw;
		margin: 0 auto;
		box-sizing: border-box;
	}

	footer {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		padding: 12px;
	}

	@media (min-width: 480px) {
		footer {
			padding: 12px 0;
		}
	}
</style>

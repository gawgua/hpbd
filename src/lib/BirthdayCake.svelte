<script lang="ts">
	import "animate.css";
	import cake from "../assets/birthdaycake.svg";
	import candle from "../assets/candle.svg";

	let candle_img: HTMLImageElement;
	let cake_img: HTMLImageElement;
	let but: HTMLButtonElement;

	function end_animation() {
		candle_img.classList.remove("animate__animated", "animate__fadeInDownBig");
		cake_img.classList.add("animate__animated", "animate__headShake");
		candle_img.classList.add("animate__animated", "animate__headShake");
	}
	function start_animation() {
		candle_img.classList.remove("hidden");
		candle_img.classList.add("animate__animated", "animate__fadeInDownBig");
		but.classList.add("animate__animated", "animate__backOutDown");
	}
</script>

<div>
	<img bind:this={candle_img} src={candle} alt="Birthday Candle" class="candle hidden" on:animationend={end_animation} />
	<img bind:this={cake_img} src={cake} alt="Birthday Cake" class="cake" />
	<br />
</div>
<div>
	<button bind:this={but} type="button" on:click={start_animation} class="">Cắm nến 🕯️</button>
</div>

<style>
	:root {
		display: flex;
		justify-content: center;
		align-items: center;
	}

	div {
		display: flex;
		justify-content: center;
		align-items: center;
	}

	button {
		font-size: 1em;
		padding: 5px 10px;
		background-color: #ce7d72;
	}

	img {
		filter: drop-shadow(0.5em 1em 8px #81564f);
	}
	img.cake {
		height: 55vh;
		max-width: 100vw;
		margin-top: 1.4em;
		margin-bottom: 1.5em;
	}
	img.candle {
		position: absolute;
		height: 55vh;
		max-width: 100vw;
	}

	.hidden {
		visibility: hidden;
	}
</style>

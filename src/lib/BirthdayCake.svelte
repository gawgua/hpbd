<script lang="ts">
	import "animate.css";
	import cake from "../assets/birthdaycake.svg";
	import candle from "../assets/candle.svg";
	import { createEventDispatcher } from "svelte";

	const dispatch = createEventDispatcher();

	let candle_img: HTMLImageElement;
	let cake_img: HTMLImageElement;
	let but: HTMLButtonElement;

	function end_animation() {
		candle_img.classList.remove("animate__fadeInDownBig");
		cake_img.classList.add("animate__headShake");
		candle_img.classList.add("animate__headShake");

		but.textContent = "Tiếp";
		but.classList.remove("animate__backOutDown");
		but.classList.add("animate__backInUp");
		but.onclick = () => {
			dispatch("next");
		};
	}
	function start_animation() {
		candle_img.classList.toggle("hidden");
		candle_img.classList.add("animate__fadeInDownBig");
		but.classList.add("animate__backOutDown");
	}
</script>

<div>
	<img
		bind:this={candle_img}
		src={candle}
		alt="Birthday Candle"
		class="candle hidden animate__animated"
		on:animationend={end_animation}
	/>
	<img bind:this={cake_img} src={cake} alt="Birthday Cake" class="cake animate__animated" />
	<br />
</div>
<div>
	<button bind:this={but} type="button" on:click={start_animation} class="animate__animated">Cắm nến 🕯️</button>
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

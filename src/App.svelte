<script lang="ts">
	import BirthdayCake from "./lib/BirthdayCake.svelte";
	import StartMenu from "./lib/StartMenu.svelte";
	import ImagesGrid from "./lib/ImagesGrid.svelte";
	import Letter from "./lib/Letter.svelte";
	import "animate.css";

	let music: HTMLAudioElement;
	let startBut: HTMLDivElement;
	let cake: HTMLDivElement;
	let imggrid: HTMLDivElement;
	let letter: HTMLDivElement;

	function animatestart_StartMenu() {
		startBut.classList.add("animate__animated", "animate__fadeOutUp");
		music.volume = 0.25;
		music.play();
	}
	function animateend_StartMenu() {
		startBut.remove();
		cake.classList.add("animate__animated", "animate__fadeInUp");
		cake.classList.remove("hidden");
	}

	function animatenext_BirthdayCake() {
		cake.classList.toggle("hidden");
		imggrid.classList.toggle("hidden");
	}

	function animatenext_grid() {
		imggrid.classList.toggle("hidden");
		letter.classList.toggle("hidden");
	}
</script>

<main>
	<audio src="./audio/hpbd.mp3" bind:this={music} loop />

	<div bind:this={startBut} on:animationend={animateend_StartMenu}>
		<StartMenu on:click={animatestart_StartMenu} />
	</div>
	<div class="hidden" bind:this={cake}>
		<BirthdayCake on:next={animatenext_BirthdayCake} />
	</div>
	<div class="hidden" bind:this={imggrid}>
		<ImagesGrid on:next={animatenext_grid} />
	</div>
	<div class="hidden" bind:this={letter}>
		<Letter />
	</div>
</main>

<style>
	.hidden {
		display: none;
	}
</style>

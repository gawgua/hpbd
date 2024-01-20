<script lang="ts">
	import BirthdayCake from "./lib/BirthdayCake.svelte";
	import StartMenu from "./lib/StartMenu.svelte";
	import "animate.css";

	let startBut: HTMLDivElement;
	let cake: HTMLDivElement;

	function animatestart_startBut() {
		startBut.classList.add("animate__animated", "animate__fadeOutUp");
	}
	function animateend_startBut() {
		startBut.remove();
		cake.classList.remove("hidden");
		cake.classList.add("animate__animated", "animate__fadeInUp");
	}
</script>

<main>
	<div bind:this={startBut} on:animationend={animateend_startBut}>
		<StartMenu on:click={animatestart_startBut} />
	</div>
	<div class="hidden" bind:this={cake}>
		<BirthdayCake />
	</div>
</main>

<style>
	.hidden {
		display: none;
	}
</style>

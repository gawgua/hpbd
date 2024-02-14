<script lang="ts">
	import { onMount } from "svelte";

	let confettiContainer: HTMLDivElement;
	let confettiClass: string;
	onMount(() => {
		setInterval(() => {
			if (!confettiClass) confettiClass = confettiContainer.childNodes[0].className;
			let confetti: HTMLDivElement = document.createElement("div");
			confetti.style.left = Math.random() * window.innerWidth + "px";
			confetti.textContent = Math.random() > 0.5 ? "🎊" : "🎉";
			confetti.className = confettiClass;
			
			while (confettiContainer.childNodes.length > (window.innerWidth >= window.innerHeight ? 30 : 15)) confettiContainer.childNodes[0].remove();
			confettiContainer.appendChild(confetti);
		}, 400);
	});
</script>

<div id="confetti-container" bind:this={confettiContainer}>
	<div class="confetti">🎉</div>
</div>

<style>
	@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500&display=swap");

	* {
		margin: 0;
		padding: 0;
		box-sizing: content-box;
		overflow: hidden;
		font-family: "Poppins", sans-serif;
	}

	#confetti-container {
		position: fixed;
		top: 0;
		left: 0;
		width: 100%;
		display: flex;
		align-items: center;
		justify-content: center;
		height: 100vh;
	}

	.confetti {
		position: absolute;
		top: 0;
		font-size: 6rem;
		animation: confetti-fall linear 5s infinite;
	}
	@keyframes confetti-fall {
		0% {
			transform: translateY(-100%) rotate(0);
		}
		100% {
			transform: translateY(100vh) rotate(180deg);
		}
	}
</style>

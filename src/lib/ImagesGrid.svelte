<script lang="ts">
	import { onMount } from "svelte";
	import { createEventDispatcher } from "svelte";
	import Confetti from "./Confetti.svelte";

	const dispatch = createEventDispatcher();

	let images: string[] = [
		"./images/grid_imgs/2.png",
		"./images/grid_imgs/4.png",
		"./images/grid_imgs/1.png",
		"./images/grid_imgs/7.png",
		"./images/grid_imgs/11.png",
		"./images/grid_imgs/12.png",
		"./images/grid_imgs/13.png",
		"./images/grid_imgs/5.png",
		"./images/grid_imgs/6.png",
		"./images/grid_imgs/3.png",
		"./images/grid_imgs/8.png",
		"./images/grid_imgs/15.png",
		"./images/grid_imgs/14.png",
		"./images/grid_imgs/16.png",
		"./images/grid_imgs/17.png",
		"./images/grid_imgs/18.png",
		"./images/grid_imgs/10.png",
		"./images/grid_imgs/9.png",
	];

	let imgArr: HTMLImageElement[] = [];
	let observer = new IntersectionObserver(
		(entries, observer) => {
			entries.forEach((e) => {
				let img: HTMLElement = e.target;
				if (e.intersectionRatio > 0.5) img.style.opacity = "1";
				else img.style.opacity = `${e.intersectionRatio / 0.5}`;
			});
		},
		{ threshold: [0, 0.1, 0.2, 0.3, 0.4, 0.5, 0.6, 0.7, 0.8, 0.9, 1] }
	);

	onMount(() => {
		imgArr.forEach((img) => observer.observe(img));
	});
</script>

<svelte:head>
	{#each images as url}
		<link rel="preload" as="image" href={url} />
	{/each}
</svelte:head>
<div class="confetti">
	<Confetti />
</div>
<h1 class="rainbow_text_animated">Gương mặt của cô nàng xinh đẹp có ngày sinh nhật hôm nay UwU</h1>
<div class="grid">
	<div class="grid-item">
		{#each images.slice(0, Math.ceil(images.length / 2)) as url, index}
			<img class="image" loading="lazy" src={url} alt="img" bind:this={imgArr[index]} />
		{/each}
	</div>
	<div class="grid-item">
		{#each images.slice(Math.ceil(images.length / 2)) as url, index}
			<img class="image" loading="lazy" src={url} alt="img" bind:this={imgArr[index + Math.ceil(images.length / 2)]} />
		{/each}
	</div>
</div>
<div class="but">
	<button on:click={() => dispatch("next")}>Có <span style="color: red; font-size:large">1</span> lời nhắn cho bạn</button>
</div>

<style>
	.confetti {
		position: relative;
		z-index: 1;
	}

	.but {
		position: relative;
		margin: 20px 0;
		display: flex;
		justify-content: center;
		z-index: 2;
	}
	button {
		background-color: #f0afa3;
		text-align: center;
		font-size: medium;
		padding: 15px 30px;
	}

	h1 {
		text-align: center;
		font-size: xx-large;
		-webkit-text-stroke-color: #ffccc2;
		-webkit-text-stroke-width: 1px;
		padding: 50px 0px;
		margin: 0;
		z-index: 1;
	}
	.rainbow_text_animated {
		background: linear-gradient(to right, #ff5837, #ff8e78, #fc3a14);
		background-size: 400% 100%;
		background-clip: text;
		color: transparent;
		animation: rainbow_animation ease-in-out 3s infinite;
	}
	@keyframes rainbow_animation {
		0%,
		100% {
			background-position: 0 0;
		}
		50% {
			background-position: 100% 0;
		}
	}

	.grid {
		display: flex;
		flex-wrap: wrap;
		padding: 0 5vw;
		z-index: 1;
	}
	.grid-item {
		flex: 25%;
		padding: 0 4px;
	}
	.grid-item .image {
		margin-top: 10px;
		vertical-align: middle;
		width: 100%;
		height: auto;
		object-fit: cover;
		opacity: 0;
	}
</style>

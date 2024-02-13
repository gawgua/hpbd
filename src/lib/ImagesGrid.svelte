<script lang="ts">
	import { onMount } from "svelte";
	import { createEventDispatcher } from "svelte";

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
				if (e.isIntersecting) img.style.opacity = "1";
				else img.style.opacity = "0";
			});
		},
		{ threshold: 0.1 }
	);

	onMount(() => {
		imgArr.forEach((img) => observer.observe(img));
	});
</script>

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
	<button on:click={() => dispatch("next")}>Có 1 lời nhắn cho bạn</button>
</div>

<style>
	.but {
		margin: 20px 0;
		display: flex;
		justify-content: center;
	}

	button {
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
	}
	.rainbow_text_animated {
		background: linear-gradient(to right, #6666ff, #0099ff, #00ff00, #ff3399, #6666ff);
		background-clip: text;
		color: transparent;
		animation: rainbow_animation 6s ease-in-out infinite;
		background-size: 400% 100%;
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
		transition: ease-in-out 300ms;
	}
</style>

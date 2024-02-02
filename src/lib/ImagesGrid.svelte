<script lang="ts">
	import Image from "./Image.svelte";

	let images: string[] = [
		"./images/grid_imgs/1.png",
		"./images/grid_imgs/2.png",
		"./images/grid_imgs/3.png",
		"./images/grid_imgs/4.png",
		"./images/grid_imgs/5.png",
		"./images/grid_imgs/6.png",
		"./images/grid_imgs/7.png",
		"./images/grid_imgs/8.png",
	];
</script>

<div class="container">
	<div class="grid">
		{#each images as img}
			<div class="grid-item">
				<Image url={img}></Image>
			</div>
		{/each}
	</div>
</div>

<style>
	.container {
		display: flex;
		justify-content: center;
		align-items: center;
	}

	.grid {
		display: grid;
		grid-template-columns: repeat(auto-fill, minmax(200px, max-content));
		grid-gap: 0.8rem;
		max-width: 900px;
		min-width: 400px;
		place-self: center;
	}

	.grid-item {
		width: 100%;
		height: 100%;
		object-fit: cover;
	}
</style>

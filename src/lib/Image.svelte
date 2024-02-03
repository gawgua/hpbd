<script lang="ts">
	import "animate.css";

	export let url: string;
</script>

<div class="image-wrapper">
	<img class="image" loading="lazy" src={url} alt="random img" />
</div>


<style>
	img:before {
		background: black;
	}
	img:active {
		opacity: 0.5;
	}

	.image {
		cursor: pointer;
		width: 100%;
		transition: 0.125s;
	}
	.image:hover {
		transform: scale(1.1);
	}
</style>

<script lang="ts">
	import { createEventDispatcher } from "svelte";
	
	const dispatch = createEventDispatcher();

	function click() {
		dispatch("click");
	}
</script>

<button type="button" class="start" on:click={click}>Ấn đi</button>

<style>
	button {
		font-size: 3em;
		padding: 30px 80px;
	}
</style>

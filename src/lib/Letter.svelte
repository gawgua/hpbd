<script lang="ts">
	import { onMount } from "svelte";

	let open = false;

	onMount(() => {
		window.onscroll = () => window.scrollTo(0, 0);
	});
</script>

<div class="container {open ? 'flap' : ''}">
	<!-- svelte-ignore a11y-click-events-have-key-events -->
	<div role="button" tabindex="-2" class="envelope-wrapper {open ? 'flap' : ''}" on:click={() => (open = !open)}>
		<div class="envelope">
			<div class="letter">
				<div class="text">
					<strong>Dear xinh ngoan yêu của anh.</strong>
					<p>
						Đến đây là hết idea rùi. Anh thấy thẩm mỹ của web này cũng gọi là hơi đuồi, nhưng mò mong là em thấy vui (OwO). Mình
						cách nhao có 3km mà như 2 du học sinh khác nước ý. Mong là mình còn iu nhao đến khi lên đại học nhe. Lúc đấy có thể
						mọi thứ sẽ thoáng hơn bây giờ. Nói chung nà chúc mừng sinh nhật nhennn.
					</p>
					<p class="sign">
						Your zaidepPhuQuoc,
						<br />Nguên.
					</p>
				</div>
			</div>
		</div>
		<div class="heart"></div>
	</div>
</div>

<style>
	p {
		margin: 0;
		opacity: 0;
		font-size: x-small;
		transition: all 0.5s ease-in-out 0.7s;
	}

	.container {
		height: 100vh;
		display: grid;
		place-items: center;
		transition: all 0.5s ease-in-out 0.7s;
	}
	.container > .envelope-wrapper {
		background: #f5edd1;
		box-shadow: 0 0 40px rgba(0, 0, 0, 0.2);
	}
	.envelope-wrapper > .envelope {
		position: relative;
		width: 300px;
		height: 230px;
	}
	.envelope-wrapper > .envelope::before {
		content: "";
		position: absolute;
		top: 0;
		z-index: 2;
		border-top: 130px solid #ecdeb8;
		border-right: 150px solid transparent;
		border-left: 150px solid transparent;
		transform-origin: top;
		transition: all 0.5s ease-in-out 0.7s;
	}
	.envelope-wrapper > .envelope::after {
		content: "";
		position: absolute;
		z-index: 2;
		width: 0px;
		height: 0px;
		border-top: 130px solid transparent;
		border-right: 150px solid #e6cfa7;
		border-bottom: 100px solid #e6cfa7;
		border-left: 150px solid #e6cfa7;
	}
	.envelope > .letter {
		position: absolute;
		right: 20%;
		bottom: 0;
		width: 54%;
		height: 80%;
		background: #ffffff;
		text-align: center;
		transition: all 1s ease-in-out;
		box-shadow: 0 0 5px rgba(0, 0, 0, 0.2);
		padding: 20px 10px;
	}

	.envelope > .letter > .text {
		font-family: "Gill Sans", "Gill Sans MT", Calibri, "Trebuchet MS", sans-serif;
		color: #444444;
		text-align: left;
		font-size: 10px;
	}
	.heart {
		position: absolute;
		top: 50%;
		left: 50%;
		width: 15px;
		height: 15px;
		background: rgb(252, 8, 231);
		z-index: 4;
		transform: translate(-50%, -20%) rotate(45deg);
		transition: transform 0.5s ease-in-out 1s;
		box-shadow: 0 1px 6px rgba(0, 0, 0, 0.2);
		cursor: pointer;
	}
	.heart:before,
	.heart:after {
		content: "";
		position: absolute;
		width: 15px;
		height: 15px;
		background-color: rgb(252, 8, 231);
		border-radius: 50%;
	}
	.heart:before {
		top: -7.5px;
	}
	.heart:after {
		right: 7.5px;
	}
	.sign {
		text-align: right;
	}
	.flap p {
		opacity: 1;
	}
	.flap.container {
		transform: translateY(100px);
	}
	.flap > .envelope:before {
		transform: rotateX(180deg);
		z-index: 0;
	}
	.flap > .envelope > .letter {
		bottom: 220px;
		transform: scale(1.5);
		transition-delay: 1s;
	}
	.flap > .heart {
		transform: rotate(225deg);
		transition-delay: 0.4s;
	}
</style>

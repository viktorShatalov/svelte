<script>
	import Modal from "./Modal.svelte";

	let isOpen = true;

	// classes
	let book__online = "book__online";
	// end classes

	const modalClose = () => {
		isOpen = false;
	};
</script>

{#if isOpen}
	<Modal {modalClose} />
{/if}

<button class:book__online on:click={() => (isOpen = true)}>Book Online</button>

<style>
	.book__online {
		position: fixed;
		bottom: 20px;
		right: 20px;
		display: block;
		background-color: yellow;
		color: black;
		font-size: 24px;
		font-weight: bold;
		z-index: 9999;
		box-shadow: rgba(0, 0, 0, 0.2) 0px 2px 4px -1px,
			rgba(0, 0, 0, 0.12) 0px 1px 10px 0px,
			rgba(0, 0, 0, 0.14) 0px 4px 5px 0px !important;
		width: 100%;
		max-width: 175px;
		padding: 10px 0;
		text-align: center;
		cursor: pointer;
		outline: none;
		border: none;
	}
</style>

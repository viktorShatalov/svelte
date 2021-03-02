<script>
	import ModalContent from "./ModalContent.svelte";

	// classes
	let modal = "modal";
	let modal__body = "modal__body";
	let modal__content = "modal__content";
	let modal__close = "modal__close";
	// end classes

	export let modalClose;

</script>

<div class:modal>
	<div class:modal__body>
		<div class:modal__content>
			<span class:modal__close on:click={modalClose} />
			<ModalContent />
		</div>
	</div>
</div>

<style>
	.modal {
		position: fixed;
		width: 100%;
		height: 100%;
		background-color: rgba(0, 0, 0, 0.6);
		top: 0;
		left: 0;
		overflow-y: auto;
		z-index: 10;
	}
	.modal__body {
		min-height: 100vh;
		display: flex;
		align-items: center;
		justify-content: center;
	}
	.modal__content {
		background-color: white;
		width: 100%;
		max-width: 60vw;
		padding: 40px 20px;
		position: relative;
		border-radius: 2px;
		margin: 40px 0;
	}
	.modal__close {
		position: absolute;
		right: 10px;
		top: 10px;
		width: 20px;
		height: 20px;
		display: block;
		cursor: pointer;
	}
	.modal__close::after,
	.modal__close::before {
		content: "";
		width: 100%;
		height: 2px;
		background-color: black;
		position: absolute;
		display: block;
		top: 9px;
		left: 0;
	}
	.modal__close::after {
		transform: rotate(45deg);
	}
	.modal__close::before {
		transform: rotate(-45deg);
	}
</style>

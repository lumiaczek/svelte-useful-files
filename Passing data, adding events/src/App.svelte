<script>
	import { tick } from 'svelte';
	import Product from "./Product.svelte";
	import Modal from "./Modal.svelte"

	let showModal = false;

	let text = "Lorem ipsum lorem"

	let closeable = false;

	let products = [
		{
			id: "p1",
			title: "A book",
			price: 9.99
		}
	]

	const addToCart = (event) => {
		console.log(event.detail);
	}

	const transform = (event) => {
		if(event.which !== 9) {
			return;
		}
		event.preventDefault();

		const selectionStart = event.target.selectionStart;
		const selectionEnd = event.target.selectionEnd;

		const value = event.target.value;

		text = value.slice(0, selectionStart) + value.slice(selectionStart, selectionEnd).toUpperCase() + value.slice(selectionEnd);

		tick().then(() => {
			event.target.selectionStart = selectionStart;
			event.target.selectionEnd = selectionEnd;
		});

	}


</script>

<button on:click={() => showModal = true}>Show Modal</button>


{#if showModal}
<Modal on:close={() => showModal = false} let:didAgree={closeable}>

		<h1 slot="header">Hello :D</h1>
		<button slot="footer" on:click={() => showModal = false} disabled={!closeable}>Close</button>

</Modal>
{/if}

<!-- <main>
	{#each products as prod}
		<Product 
		{...prod}
		on:add-to-cart={addToCart}
		on:delete={() => {alert('Deleted!')}}	
		/>
	{/each}

</main> -->

<textarea rows="5" value={text} style="display:block;" on:keydown={transform}></textarea>

<style>

</style>
<script>
	import Product from "./Product.svelte";
	import CartItem from "./CartItem.svelte";

	

	let renderComponent = {
		cmp: Product,
		title: "A product",
		id: "p1"
	}

	const toogle = () => {
		if(renderComponent.cmp === Product){
			renderComponent = {cmp: CartItem, title: "Test product", id: "p2" }
		} else{
			renderComponent = { cmp: Product, title: "A product", id: "p1" }
		}
	}
</script>

<button on:click={toogle}>Toggle display</button>


<svelte:component this={renderComponent.cmp} title={renderComponent.title} id={renderComponent.id}/>

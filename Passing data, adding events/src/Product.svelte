<script>
    export let title;
    export let price;
    import { createEventDispatcher } from 'svelte';

    const dispach = createEventDispatcher();

    const addToCart = () => {
        dispach('add-to-cart', {
            id: 'p1'
        });
    }

    const deleteFromCart = () => {
        dispach('delete', "p1");
    }

</script>

<article>
    <h1>{title}</h1>
    <h3>${price}</h3>
    <button on:click={addToCart}>Add to cart</button>
    <button on:click={deleteFromCart}>Delete</button>
</article>
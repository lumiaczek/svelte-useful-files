<script>
  import CartItem from "./CartItem.svelte";
  import cart from "./cart-store.js";
  import { onDestroy } from 'svelte';

  // let items;

  // const unsubscribe = cart.subscribe(its => {
  //   items = its;
  // });

  // onDestroy(() => {
  //   if(unsubscribe){
  //     unsubscribe();
  //   }
  // })

  const removeFromCart = (event) => {
    const id = event.detail;

    cart.removeItem(id);

  }
    

</script>

<style>
  section {
    width: 30rem;
    max-width: 90%;
    margin: 2rem auto;
    border-bottom: 2px solid #ccc;
  }

  ul {
    list-style: none;
    margin: 0;
    padding: 0;
  }
</style>

<section>
  <h1>Cart</h1>
  <ul>
    {#each $cart as item (item.id)}
      <CartItem id={item.id} title={item.title} price={item.price} on:remove={removeFromCart}/>
    {:else}
      <p>No items in cart yet!</p>
    {/each}
  </ul>
</section>

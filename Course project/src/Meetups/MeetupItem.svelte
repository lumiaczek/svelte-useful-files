<script>

    import { createEventDispatcher } from "svelte";

    const dispatch = createEventDispatcher();

    import Button from "../UX/Button.svelte";


    export let id;
    export let title;
    export let subtitle;
    export let description;
    export let address;
    export let isFav;
</script>

<article>
    <header>
        <h1>{title}</h1>
        <h2>{subtitle}</h2>
    </header>
    <div class="image"></div>
    <div class="content">
        <p>{description}</p>
        <p class="address">{address}</p>
    </div>
    <footer>
        <Button caption={"Show details"} on:click={() => dispatch('toggleFavorite', id)}/>
        <Button caption={isFav ? "Unfavorite" : "Favorite"} />
    </footer>
</article>

<style>

    * {
        font-family: Verdana, Geneva, Tahoma, sans-serif;
    }

    article {
        box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
        border-radius: 15px;
        background-color: white;
        margin: 1rem;
    }

    header,
    .content,
    footer {
        padding: 1rem;
    }

    .image{
        width: 100%;
        height: 14rem;
        background-color: gray; 
        opacity: 1;
    }

    h2 {
        font-size: 1rem;
        color: #808080;
        margin: 0.5rem 0;
    }

    p{
        font-size: 1.25rem;
        margin: 0;
    }

    div {
        text-align: right;
    }

    .address {
        font-size: small;
        color: gray;
    }

</style>
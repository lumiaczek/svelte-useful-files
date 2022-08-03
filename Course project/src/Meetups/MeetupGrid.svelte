<script>
    import MeetupItem from "./MeetupItem.svelte";
    export let meetups;
</script>

<section class="meetups">
	{#each meetups as meetup}
		<MeetupItem
        id={meetup.id}
		title={meetup.title}
		subtitle={meetup.subtitle}
		description={meetup.description}
		address={meetup.address}
        isFav = {meetup.isFavorite}
        on:toggleFavorite
		/>
	{/each}
</section>

<style>
	.meetups {
		margin-top: 5rem;
	}

    section {
        width: 100%;
        display: grid;
        grid-template-columns: 1fr;
        grid-gap: 0.25rem;
    }

    @media (min-width: 768px){
        section {
            grid-template-columns: repeat(2, 1fr);
        }
    }
</style>
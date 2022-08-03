<script>

	import Header from "./UI/Header.svelte";
	import MeetupGrid from "./Meetups/MeetupGrid.svelte";
	import Button from "./UX/Button.svelte";

	let meetups = [
		{
			id: 'm1',
			title: 'Coding Bootcamp',
			subtitle: 'Learn to code in 2 hours',
			description: 'Lorem ipsum dolor, sit amet consectetur adipisicing elit. Tempore minus incidunt iste. Perferendis consequatur suscipit facere tenetur provident praesentium quas voluptatem? Deleniti, ab enim beatae totam quibusdam suscipit tempora omnis.',
			address: '28th Nerd Road, 32543 New York',
			isFavorite: false
		},
		{
			id: 'm2',
			title: 'Gym workout',
			subtitle: 'Get in shape!',
			description: 'Lorem ipsum dolor, sit amet consectetur adipisicing elit. Tempore minus incidunt iste. Perferendis consequatur suscipit facere tenetur provident praesentium quas voluptatem? Deleniti, ab enim beatae totam quibusdam suscipit tempora omnis.',
			address: '28th Nerd Road, 32543 New York',
			isFavorite: false
		}
	]

	let title = '';
	let subtitle = '';
	let description = '';
	let address = '';

	const handleFormSubmit = () => {
		
		const newMeetup = {
			id: Math.random().toString(),
			title: title,
			subtitle: subtitle,
			description: description,
			address: address
		}

		meetups = [newMeetup, ...meetups];

		console.table(meetups);
	}

	const toggleFavorite = (event) =>{
		const id = event.detail;
		const updatedMeetup = {...meetups.find(m => {m.id === id})};
		updatedMeetup.isFavorite = !updatedMeetup.isFavorite;
		const meetupIndex = meetups.findIndex(m => m.id === id);
		const updatedMeetups = [...meetups];
		updatedMeetups[meetupIndex] = updatedMeetup;
		meetups = updatedMeetups;
	}

</script>

<div class="formularz">
	<form on:submit|preventDefault={handleFormSubmit} style="width: 30rem;">
		<div class="form-control">
			<label for="title">Title</label>
			<input type="text" id="title" bind:value={title}/>
		</div>
		<div class="form-control">
			<label for="subtitle">Subtitle</label>
			<input type="text" id="subtitle" bind:value={subtitle}/>
		</div>
		<div class="form-control">
			<label for="address">Address</label>
			<input type="text" id="address" bind:value={address}/>
		</div>
		<div class="form-control">
			<label for="description">Description</label>
			<textarea id="description" rows="3" bind:value={description}></textarea>
		</div>
		<div style="display: flex; align-items: center; justify-content: center;"><Button type={"submit"} caption={"Dodaj"}/></div>
	</form>
</div>

<Header/>
<MeetupGrid {meetups} on:toggleFavorite={toggleFavorite}/>

<style>
	* {
		font-family: Verdana, Geneva, Tahoma, sans-serif;
	}

	.form-control input {
		width: 100%;
		padding: 0.5rem;
		border-radius: 10px;
		border: 1px solid rgb(173, 173, 173);
	}

	.form-control input:focus{
		border: 2px solid white;
		border-bottom: 2px solid rgb(255, 0, 98);
		outline: none;
	}

	.form-control input:active{
		border: 2px solid white;
		border-bottom: 2px solid rgb(255, 0, 98);
		outline: none;
	}

	.form-control textarea:focus{
		border: 2px solid white;
		border-bottom: 2px solid rgb(255, 0, 98);
		outline: none;
	}

	.form-control textarea:active{
		border: 2px solid white;
		border-bottom: 2px solid rgb(255, 0, 98);
		outline: none;
	}

	.form-control {
		margin: 1.2rem;
	}

	.form-control textarea{
		width: 100%;
		padding: 0.5rem;
		border-radius: 10px;
		border: 1px solid rgb(173, 173, 173);
	}

	.form-control label{
		display: block;
	}

	.formularz {
		display: flex;
		height: 100%;
		width: 100%;
		margin-top: 5rem;
		justify-content: center;
		align-items: center;
	}


</style>


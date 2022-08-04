<script>

	import { onMount } from 'svelte';
	import hobbyStore from './hobby-store.js';

	let hobbies = [];
	let hobbyInput;
	let isLoading = false;

	onMount(() => {
	fetch('https://svelte-130dc-default-rtdb.europe-west1.firebasedatabase.app/hobbies.json')
		.then(response => {
			if(!response.ok){
				throw new Error("Failed at data fetching!");
			}
			return response.json();
		})
		.then(data => {
			// hobbies = Object.values(data);

			hobbyStore.setHobbies(Object.values(data));

			// return hobbies;
		})
		.catch(err => {
			console.error(err);
		})
	});

	const addHobby = () => {
		// hobbies = [...hobbies, hobbyInput];

		hobbyStore.addHobby(hobbyInput);

		isLoading = true;
		fetch('https://svelte-130dc-default-rtdb.europe-west1.firebasedatabase.app/hobbies.json',{
			method: 'POST',
			body: JSON.stringify(hobbyInput),
			headers: {
				'Content-Type': 'application/json'
			}
		}).then(response => {
			isLoading = false;
			if (!response.ok){
				throw new Error('Failed!');
			}
			console.log("Data saved!");
		}).catch(err => {
			isLoading = false;
			console.log(err);
		});
	}
</script>

<label for="hobby">Hobby</label>
<input type="text" id="hobby" bind:value={hobbyInput}>
<button on:click={addHobby}>Add hobby</button>

{#if isLoading}
	<p>Loading...</p>

{:else}
<ul>
	{#each $hobbyStore as hobby}
	<li>{hobby}</li>
	{/each}
</ul>
{/if}

<!-- {#await getHobbies}
<p>Loading...</p>
{:then hobbyData}
<ul>
	{#each hobbyData as hobby}
	<li>{hobby}</li>
	{/each}
</ul>
{:catch error}
<p>{error.message}</p>
{/await} -->
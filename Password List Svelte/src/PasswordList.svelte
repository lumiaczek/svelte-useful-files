<script>

        // ! Opracowany koncept usuwania poszczególnych przedmiotów z listy : Do późniejszego wykorzystania bo robiłem to chyba z godzine xD

	let password = "";
	let passwords = [];

    // ze względu na budowe Svelte, funkcja Array.pop() nie da tutaj rezultatu, więc używając spread'a odświeżamy zawartość tablicy tak aby #each go złapał

	const addToArray = () => {
		passwords = [...passwords, {
			pass: password,
			id: Math.random()
		}];
	}

    // znajdujemy index który posiada dane id i usuwamy go po czym odświeżamy zawartość tablicy

	const removeFromList = (id) => {
		const index = passwords.findIndex(password => password.id == id);
		console.log(index);
		passwords.splice(index, 1);
		passwords = [...passwords]; // tak to jest potrzebne, sprawdziłem to xD
		console.log(passwords);
	}
</script>

<main>
	<button on:click={addToArray} style="margin-bottom:1rem;">
		Add to array!
	</button><br>
	<input type="password" name="pass" bind:value={password}>
	<ul>

        <!-- pętla each która wyświetla właściwości pw.pass oraz posiada identyfikator unikany przez co wszystkie elementy się na nowo nie renderują
        dodatkowo button bo fajny :D -->

		{#each passwords as pw, i (pw.id)}
		<div>
			<li>{pw.pass}</li>
			<button on:click={() => {removeFromList(pw.id)}}>Usuń {pw.pass}</button>
		</div>
		{/each}
	</ul>
</main>

<style>
	li {
		width: fit-content;
	}
</style>
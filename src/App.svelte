<script>
	import Modal from "./Modal.svelte";

	let people = [
		{ name: "yoshi", beltColour: "black", age: 25, id: 1 },
		{ name: "mario", beltColour: "orange", age: 45, id: 2 },
		{ name: "luigi", beltColour: "brown", age: 35, id: 3 },
	];

	const handleDelete = (id) => {
		people = people.filter((person) => person.id != id);
	};

</script>

<Modal/>

<main>
	{#each people as person (person.id)}
		<div>
			<h4>{person.name}</h4>
			{#if person.beltColour === 'black'}
			<p><strong>MASTER NINJA</strong></p>
			{/if}
			<p>
				{person.age} years old, {person.beltColour} belt. - {person.id}
			</p>
			<button on:click={() => handleDelete(person.id)}> Delete </button>
		</div>
	{:else}
		<p>There are no people to show...</p>
	{/each}
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	/* h4 {
		color:blue;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	} */

	:global(img) {
		opacity: 0.9;
		transition: all 0.2s;
	}
	:global(img):hover {
		opacity: 1;
		transform: scale(1.04);
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>

<script>
	import Modal from "./Modal.svelte";
	import AddPersonForm from "./AddPersonForm.svelte";
	let showModal = false;
	let people = [
		{name: "yoshi", beltColor: "black", age: 25, id: 1},
		{name: "mario", beltColor: "orange", age: 45, id: 2},
		{name: "luigi", beltColor: "brown", age: 35, id: 3},
	];
	const handleClick = (id) => {
		people = people.filter((person) => person.id != id);
	}
	let num = 5;
	const toggleModal = () => {
		showModal = !showModal;
	}

	const addPerson = (e) => {
		// console.log(e.detail);
		const person = e.detail;
		people = [person, ...people];
	}
</script>

<Modal {showModal} on:click={toggleModal}>
	<AddPersonForm on:addPerson={addPerson} />
</Modal>
<main>
	<button on:click|once={toggleModal}>Open Modal</button>
	<div>
		{#each people as person (person.id)}
			<div>
				{#if person.beltColor === "black"}
					<p><strong>Sensei</strong></p>
				{/if}
				<h4>{person.name}</h4>
					
				<p>{person.age} years old, {person.beltColor} belt.</p>
				<button on:click = {() => {handleClick(person.id)}}>Delete</button>
			</div>
		{:else}
			<p>No people to show.</p>
		{/each}
	</div>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>
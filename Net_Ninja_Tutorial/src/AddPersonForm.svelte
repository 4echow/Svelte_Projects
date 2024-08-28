<script>
    import { createEventDispatcher } from "svelte";

    let dispatch = createEventDispatcher();

    let name;
    let beltColor;
    let age;
    // let fighting = false;
    // let sneaking = false;
    // let running = false;
    let skills = [];

    const handleSubmit = () => {
        const person = {
            name,
            beltColor,
            age,
            skills,
            id: Math.random()
        }
        dispatch("addPerson", person);
    }
</script>


<form on:submit|preventDefault={handleSubmit}>
    <input type="text" placeholder="name" bind:value={name}><br>
    <!-- <input type="text" placeholder="belt color" bind:value={beltColor}><br> -->
    <input type="number" placeholder="age" bind:value={age}><br>
    <!-- svelte-ignore a11y-label-has-associated-control -->
    <label>Skills:</label>
    <!-- <input type="checkbox" bind:checked={fighting}>fighting<br>
    <input type="checkbox" bind:checked={sneaking}>sneaking<br>
    <input type="checkbox" bind:checked={running}>running<br> -->
    <input type="checkbox" bind:group={skills} value="fighting">fighting<br>
    <input type="checkbox" bind:group={skills} value="sneaking">sneaking<br>
    <input type="checkbox" bind:group={skills} value="running">running<br>
    <select bind:value={beltColor}>
        <option value="black">black</option>
        <option value="brown">brown</option>
        <option value="orange">orange</option>
        <option value="white">white</option>
    </select>
    <button>Add person</button>
</form>

<style>
</style>
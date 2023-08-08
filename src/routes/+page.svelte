<!-- YOU CAN DELETE EVERYTHING IN THIS PAGE -->
<script>
	import { onMount } from 'svelte';

	async function getTickets() {
		const res = await fetch('http://localhost:8080/api/tickets');
		const data = await res.json();
		return data;
	}

	let tickets = [];

    onMount(async () => {
        tickets = await getTickets();
    });

	console.log(tickets);
</script>

<div>
	<!-- <form>
		<input class="input mb-2" type="text">
		<input class="input mb-2" type="password">
		<button class="btn variant-filled" type="submit">Submit</button>
	</form> -->
	{#each tickets as ticket}
	<div class="card shadow-xl m-4">
		<header class="card-header">{ticket.Name}</header>
		<section class="p-4">{ticket.Description}</section>

	</div>
	{/each}
</div>

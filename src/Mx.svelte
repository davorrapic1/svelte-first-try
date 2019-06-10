<script>

export let mxRecords = [];


</script>

	{#if mxRecords.length > 0}
	{#each mxRecords as mx}
	<h3> Mx record is: {mx.mxRecord}</h3>
	{/each}
	{:else}
	<h1>no email data to show</h1>
	{/if}
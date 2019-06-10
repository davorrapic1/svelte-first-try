<script>

export let aRecords = [];

</script>


<div>
	{#if aRecords.length > 0}
	{#each aRecords as host}
	<h3> Server name is: {host.hostName}</h3>
	<h3>Server IP is: {host.hostIp}</h3>
	{/each}
	{:else}
	<h1>no web data to show</h1>
	{/if}
</div>
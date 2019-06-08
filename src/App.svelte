<script>

	import axios from 'axios';
	import { onMount } from 'svelte';

	let domain = '';
	let webData = [];
	let mxData = [];



	function getRecords() {
		axios.get('http://tracker.mycode.com.hr/api/values/' + domain.trim()).then(res => {
		webData = res.data.webHostData;
		mxData = res.data.emailData;
	})
	}

</script>

<style>
	
</style>

<div>
	<div>
		<input bind:value={domain} placeholder="Enter your domain here">
		<button on:click={getRecords}> Get Dns records</button>
	</div>

	{#if webData.length > 0}
	{#each webData as data}
	<h3> Server name is: {data.hostName}</h3>
	<h3>Server IP is: {data.hostIp}</h3>
	{/each}
	{:else}
	<h1>no web data to show</h1>
	{/if}

	{#if mxData.length > 0}
	{#each mxData as data}
	<h3> Mx record is: {data.mxRecord}</h3>
	{/each}
	{:else}
	<h1>no email data to show</h1>
	{/if}

</div>


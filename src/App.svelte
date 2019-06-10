<script>


	import Host from './Host.svelte';
	import Mx from './Mx.svelte';
	import axios from 'axios';
	import { onMount } from 'svelte';

	let baseUrl = 'http://tracker.mycode.com.hr/api/values/';
	let domain = '';
	let webData = [];
	let mxData = [];



	function getRecords() {
		axios.get(baseUrl + domain.trim()).then(res => {
		webData = res.data.webHostData;
		mxData = res.data.emailData;
	})
	}

</script>

<style>

.page {
	height: 100%;
	width: 100%;
	align-items: center;
	display: flex;
	justify-content: center;
	flex-direction: column;

	}
	
</style>

<div class="page">
<div class="container">
	<div>
		<input bind:value={domain} placeholder="Enter your domain here">
		<button on:click={getRecords}> Get Dns records</button>
	</div>

	<Host aRecords={webData} />

	<Mx mxRecords={mxData} />
	</div>
</div>


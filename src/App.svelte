<script>
	import Header from "./components/Header.svelte";
	import Footer from "./components/Footer.svelte";
	import Tabs from "./shared/Tabs.svelte";
	import CreatePollForm from "./components/CreatePollForm.svelte";
	import PollList from "./components/PollList.svelte";

	//tabs
	let items = ['Current Polls','Add New Poll'];
	let activeItems = 'Current Polls';

	const tabChange = (e) => {
		activeItems = e.detail;
	}

	const handleAdd = (e) => { 
		activeItems = 'Current Polls';
	}

</script>

<Header />
<main>
	<Tabs {activeItems} {items} on:tabChange={tabChange}/>
	{#if activeItems === 'Current Polls'}
		<PollList/>
		{:else if activeItems === 'Add New Poll'}
			<CreatePollForm on:add={handleAdd}/>
	{/if}
</main>
<Footer />

<style> 
	main {
		max-width: 960px;
		margin: 40px auto;
	}
</style>
<script>
	import Header from "./components/Header.svelte";
	import Footer from "./components/Footer.svelte";
	import Tabs from "./shared/Tabs.svelte";
	import CreatePollForm from "./components/CreatePollForm.svelte";

	//tabs
	let items = ['Current Polls','Add New Poll'];
	let activeItems = 'Current Polls';

	const tabChange = (e) => {
		activeItems = e.detail;
	}
</script>

<Header />
<main>
	<Tabs {activeItems} {items} on:tabChange={tabChange}/>
	{#if activeItems === 'Current Polls'}
		<p>Poll list Component Goes Here</p>
		{:else if activeItems === 'Add New Poll'}
			<CreatePollForm />
	{/if}
</main>
<Footer />

<style>
	main {
		max-width: 960px;
		margin: 40px auto;
	}
</style>
<script>
	import Header from './components/Header.svelte'
	import Footer from './components/Footer.svelte'
	import Tabs from './shared/Tabs.svelte'
	import CreatePollForm from './components/CreatePollForm.svelte'
	import PollList from './components/PollList.svelte'

	// tabs
	let items = ["Current Polls", "Add New Poll"];
	let activeItem = "Current Polls"

	const tabChange = (e) => {
		activeItem = e.detail // detail은 dispatch에 넣어준 값 그대로
	}

	const handleAdd = () => {
		activeItem = "Current Polls"
	}
</script>

<Header/>
	<main>
		<Tabs activeItem={activeItem} items={items} on:tabChange={tabChange} />
		{#if activeItem === "Current Polls"}
			<PollList />
		{:else if activeItem === "Add New Poll"}
			<CreatePollForm on:add={handleAdd}/>
		{/if}
	</main>
<Footer/>

<style>
main {
	max-width: 960px;
	margin: 40px auto;
}

</style>
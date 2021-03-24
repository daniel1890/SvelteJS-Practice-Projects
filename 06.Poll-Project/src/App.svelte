<script>
	import Header from './components/Header.svelte';
	import Footer from './components/Footer.svelte';
	import Tabs from './shared/Tabs.svelte';

	// tabs
	let items = ['Current Polls', 'Add New Poll'];
	let activeItem = 'Current Polls';
</script>

<Header />
<main>
	<!-- Op deze manier pass je data als properties mee aan een component. -->
	<Tabs {activeItem} {items} />
</main>
<Footer />


<style>
	main {
		max-width: 75rem;
		margin: 40px auto;
	}
</style>
<script lang="ts">
	import '../app.css';
	import NavBar from '../components/NavBar.svelte';
	let { children } = $props();
</script>

<div class="bg-[url(/background.jpg)] bg-fixed">
	<NavBar />
	{@render children()}
</div>

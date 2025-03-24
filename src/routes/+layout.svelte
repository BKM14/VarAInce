<script lang="ts">
	import '../app.css';
	let { children } = $props();
</script>

<div class="bg-[url(/bg.png)] bg-fixed bg-cover bg-no-repeat">
	{@render children()}
</div>

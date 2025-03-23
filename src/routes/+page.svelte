<script lang="ts">
	import Timeline from '../components/Timeline.svelte';
    import Footer from '../components/Footer.svelte';
	import Headline from '../components/Headline.svelte';
</script>

<div class="min-h-screen flex flex-col justify-center items-center">
    <div class="flex min-h-screen items-center justify-center text-7xl text-white font-extrabold">
        Main SVG
    </div>
	<div class="flex min-h-screen items-center justify-center">
        <Timeline />
    </div>
    <Headline />
    <Footer />
</div>

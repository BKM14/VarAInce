<script lang="ts">
	import { onMount } from "svelte";

	let visible = false;
	let element: HTMLElement | null = null;

	function handleIntersection(entries: IntersectionObserverEntry[]) {
		for (const entry of entries) {
			visible = entry.isIntersecting;
		}
	}

	onMount(() => {
		const observer = new IntersectionObserver(handleIntersection, { threshold: 0.3 });
		if (element) observer.observe(element);

		return () => observer.disconnect();
	});
</script>


<div class="flex justify-end w-full md:w-2/3 px-4 md:px-6 text-orange-600" bind:this={element}>
    <div class="{visible ? 'fade-visible' : 'fade-hidden'}">
        <h2 class="text-3xl md:text-5xl lg:text-6xl font-bold mb-4 md:mb-6 lg:mb-8">
            About VarAInce Week
        </h2>
        <p class="text-base md:text-lg lg:text-2xl md:text-left mb-8">
            CodeForge AI Hackathon, organized by VarAInce Club—the AI and Data Science Club at BMSCE—is an adrenaline-pumping, mind-bending 
            competition where innovation meets intelligence! This hackathon challenges participants to push the limits of their creativity and 
            technical skills, creating AI-driven solutions to real-world problems.
        </p>
        <p class="text-base md:text-lg lg:text-2xl md:text-left mb-8">
            Whether you're crafting cutting-edge machine learning models, building powerful applications, or experimenting with advanced 
            algorithms, this is the place to showcase your potential.
        </p>
        <p class="text-base md:text-lg lg:text-2xl md:text-left mb-8">
            Ready to forge the future with AI? Assemble your team, ignite your passion, and let your ideas take flight in CodeForge AI Hackathon—where innovation meets impact!
        </p>
    </div>
</div>
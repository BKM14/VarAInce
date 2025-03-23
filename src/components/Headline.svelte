<script lang="ts">
	import { onMount } from "svelte";
	import { fade } from "svelte/transition";

    let visible = false;
    let element: HTMLElement | null = null

    onMount(() => {
        const observer = new IntersectionObserver(
            ([entry]) => (visible = entry.isIntersecting),
            {threshold: 0.30}
        )
        observer.observe(element!);
    });
</script>

<div class=" flex flex-col w-full md:w-2/3 px-4 md:px-6 min-h-screen text-orange-600" bind:this={element}>
    {#if visible}
    <div transition:fade={{duration: 300}}>
        <h2 class="text-center text-3xl md:text-5xl lg:text-6xl font-bold mb-4 md:mb-6 lg:mb-8">
            About Cryptic Hunt 3.0 - VIT's Largest Scavenger Hunt!
        </h2>
        <p class="text-base md:text-lg lg:text-2xl text-center md:text-left mb-8">
            Cryptic Hunt 3.0, is a thrilling campus-wide scavenger hunt like no other! This event challenges participants to solve cryptic riddles, uncover hidden clues, and scan QR codes scattered throughout the VIT campus. With the help of our dedicated app, you'll explore the campus, unravel mysteries, and compete for victory.
        </p>
        <p class="text-base md:text-lg lg:text-2xl text-center md:text-left m-4">
            Prepare yourself for the most electrifying event VIT has ever seen—Cryptic Hunt 3.0, where the stakes are high, the challenges are fierce, and only the sharpest minds will prevail!
        </p>
        <p class="text-base md:text-lg lg:text-2xl text-center md:text-left mb-8">
            Ready to test your wits and embark on an adventure? Download the app and be a part of the action!
        </p>
    </div>
    {/if}
</div>
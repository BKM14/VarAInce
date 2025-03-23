<script lang="ts">
	import { Timeline, TimelineItem } from 'flowbite-svelte';
	import { onMount } from 'svelte';
	import { blur, fly, scale, slide } from 'svelte/transition';
    let element: HTMLElement | null = null;
    let visible = false;

    onMount(() => {
        const observer = new IntersectionObserver(
            ([entry]) => (visible = entry.isIntersecting),
            {threshold: 0.30}
        );
        observer.observe(element!);
    });

	const events = [
		{
			title: 'Flowbite Application UI v2.0.0',
			date: 'Released on January 13th, 2022',
			description: 'Get access to over 20+ pages.'
		},
		{
			title: 'Flowbite Figma v1.3.0',
			date: 'Released on December 7th, 2021',
			description: 'All of the pages and components are first designed in Figma. '
		},
		{
			title: 'Flowbite Library v1.2.2',
			date: 'Released on December 2nd, 2021',
			description: 'Interactive elements built on top of Tailwind CSS.'
		}
	];
</script>

<div bind:this={element}>
    {#if visible}
    <div transition:blur={{duration: 700}}>
        <Timeline order="vertical" >
            {#each events as event (event.title)}
                <TimelineItem title={event.title} date={event.date} classH3="text-white" classTime="text-white">
                    <svelte:fragment slot="icon">
                        <span
                            class="bg-primary-200 dark:bg-primary-900 absolute -start-3 flex h-6 w-6 items-center justify-center rounded-full ring-8 ring-white dark:ring-gray-900"
                        >
                            <div class="text-primary-600 dark:text-primary-400 h-4 w-4"></div>
                        </span>
                    </svelte:fragment>
                    <p class="mb-4 text-base font-normal text-white">{event.description}</p>
                </TimelineItem>
            {/each}
        </Timeline>
    </div>
    {/if}
</div>


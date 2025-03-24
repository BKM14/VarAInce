<script lang="ts">
	import { Modal, Timeline, TimelineItem } from 'flowbite-svelte';
	import { onMount, tick } from 'svelte';
	import { blur } from 'svelte/transition';
    let element: HTMLElement | null = null;
    let visible = false;
    let showModal = false;


    onMount(() => {
        const observer = new IntersectionObserver(
            async ([entry]) => {
                await tick();
                (visible = entry.isIntersecting)
            },
            {threshold: 0.30}
        );
        observer.observe(element!);

        return () => observer.disconnect();
    });

    interface Event {
        title: string,
        date: string,
        description: string,
        googleFormsLink: string
    }

    let selectedEvent: Event | null = null;

    function openModal(event: Event) {
        selectedEvent = event;
        showModal = true;
    }

	const events: Event[] = [
		{
			title: 'Flowbite Application UI v2.0.0',
			date: 'Released on January 13th, 2022',
			description: 'Get access to over 20+ pages.',
            googleFormsLink: "https://docs.google.com/forms/d/e/1FAIpQLSfIJFjekV1729WLJy0lyF17dA2DIpsg5oJR4uW8F1XJR22S0w/viewform?embedded=true"
		},
		{
			title: 'Flowbite Figma v1.3.0',
			date: 'Released on December 7th, 2021',
			description: 'All of the pages and components are first designed in Figma.',
            googleFormsLink: "https://docs.google.com/forms/d/e/1FAIpQLSfIJFjekV1729WLJy0lyF17dA2DIpsg5oJR4uW8F1XJR22S0w/viewform?embedded=true"
		},
		{
			title: 'Flowbite Library v1.2.2',
			date: 'Released on December 2nd, 2021',
			description: 'Interactive elements built on top of Tailwind CSS.',
            googleFormsLink: "https://docs.google.com/forms/d/e/1FAIpQLSfIJFjekV1729WLJy0lyF17dA2DIpsg5oJR4uW8F1XJR22S0w/viewform?embedded=true"
		}
	];
</script>

<div bind:this={element}>
    {#if visible}
    <div transition:blur={{duration: 700}}>
        <p class="font-bold text-center text-6xl text-white m-20">Timeline of events</p>
        <Timeline order="vertical" class="md:ml-45 ml-20">
            {#each events as event (event.title)}
            <button on:click={() => openModal(event)} class="cursor-pointer flex flex-col">
                <TimelineItem 
                    title={event.title} 
                    date={event.date} 
                    classH3="text-white" 
                    classTime="text-white"
                >
                    <svelte:fragment slot="icon">
                        <span class="bg-primary-200 dark:bg-primary-900 absolute -start-3 flex h-6 w-6 
                                      items-center justify-center rounded-full ring-8 ring-white dark:ring-gray-900">
                            <div class="text-primary-600 dark:text-primary-400 h-4 w-4"></div>
                        </span>
                    </svelte:fragment>
                    <p class="mb-4 text-base font-normal text-white">{event.description}</p>
                </TimelineItem>
            </button>                
            {/each}
        </Timeline>
    </div>
    {/if}
</div>

<Modal bind:open={showModal} size="md" outsideclose class="bg-slate-500">
    <div class="p-6 bg-slate-70 flex flex-col justify-center items-center">
      {#if selectedEvent}
        <h3 class="text-xl font-bold text-gray-900 dark:text-white">{selectedEvent.title}</h3>
        <p class="mt-2 text-gray-700 dark:text-gray-300">{selectedEvent.description}</p>
        <p class="mt-2 text-sm text-gray-500 dark:text-gray-400">{selectedEvent.date}</p>
        <iframe title="Register Here" src="https://docs.google.com/forms/d/e/1FAIpQLSfIJFjekV1729WLJy0lyF17dA2DIpsg5oJR4uW8F1XJR22S0w/viewform?embedded=true" width="640" height="1501" frameborder="0" marginheight="0" marginwidth="0">Loading…</iframe>
      {/if}
      <button on:click={() => (showModal = false)} class="mt-4 w-full bg-blue-500 text-white p-2 rounded">
        Close
      </button>
    </div>
</Modal>

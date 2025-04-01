<script lang="ts">
	import { Modal, Timeline, TimelineItem, Button } from 'flowbite-svelte';
	import { onMount } from 'svelte';
    let element: HTMLElement | null = null;
    let visible = false;
    let showModal = false;

    function handleIntersection(entries: IntersectionObserverEntry[]) {
    for (const entry of entries) {
        if (entry.isIntersecting) {
            visible = true;
        } else {
            visible = false;
        }
    }
}


    onMount(() => {
        const observer = new IntersectionObserver(handleIntersection, { threshold: 0.3 });
        if (element) observer.observe(element);

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
			description: 'Get access to over 20+ pages.',
            googleFormsLink: "https://docs.google.com/forms/d/e/1FAIpQLSfIJFjekV1729WLJy0lyF17dA2DIpsg5oJR4uW8F1XJR22S0w/viewform?embedded=true"
		},
		{
			title: 'Flowbite Library v1.2.2',
			date: 'Released on December 2nd, 2021',
			description: 'Get access to over 20+ pages.',
            googleFormsLink: "https://docs.google.com/forms/d/e/1FAIpQLSfIJFjekV1729WLJy0lyF17dA2DIpsg5oJR4uW8F1XJR22S0w/viewform?embedded=true"
		}
	];
</script>

<div bind:this={element} class="{visible ? 'timeline-visible' : 'timeline-hidden'} max-w-screen">
    <p class="font-bold text-center text-6xl text-white p-10">Timeline of events</p>
    <Timeline order="vertical" class="md:ml-45 ml-10">
        {#each events as event (event.title)}
        <button on:click={() => openModal(event)} class="cursor-pointer flex flex-col">
            <TimelineItem 
                title={event.title} 
                date={event.date} 
                classH3="text-white" 
                classTime="text-white flex"
            >
                <svelte:fragment slot="icon">
                    <span class="bg-primary-200 dark:bg-primary-900 absolute -start-3 flex h-6 w-6
                                  items-center justify-center rounded-full ring-8 ring-white dark:ring-gray-900">
                        <div class="text-primary-600 dark:text-primary-400 h-4 w-4"></div>
                    </span>
                </svelte:fragment>
                <p class="mb-4 font-normal text-white">{event.description}</p>
            </TimelineItem>
        </button>                
        {/each}
    </Timeline>
</div>


<Modal bind:open={showModal} size="md" outsideclose>
    <div class="p-6 bg-slate-70 flex flex-col justify-center items-center bg-white">
      {#if selectedEvent}
        <h3 class="text-xl font-bold text-gray-900 dark:text-white">{selectedEvent.title}</h3>
        <p class="mt-2 text-gray-700 dark:text-gray-300">{selectedEvent.description}</p>
        <p class="mt-2 text-sm text-gray-500 dark:text-gray-400">{selectedEvent.date}</p>
        <Button color="green" class="mt-4 w-full"> 
            <a href={selectedEvent.googleFormsLink} target="_blank">Register Here</a>
        </Button>
      {/if}

    </div>
  </Modal>

<script lang="ts">
	import { Modal, Button } from 'flowbite-svelte';
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
        const observer = new IntersectionObserver(handleIntersection, { threshold: 0.1 });
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
			title: 'Lol-Garithms',
			date: '2nd April, 10AM - 1PM',
			description: 'Where AI meets Memes',
            googleFormsLink: "https://forms.gle/nw6cqbWqqgCkKuaj9"
		},
		{
			title: 'DecodeAI',
			date: '2nd April, 11AM - 1PM',
			description: 'Decode the Future, One AI Challenge at a Time!',
            googleFormsLink: "https://forms.gle/dEmdexATzsZCdiAg6"
		},
		{
			title: 'Exploring RAGs',
			date: '2nd April, 2PM - 4PM',
			description: 'Uncover the Power of AI - Dive Deep, Get Hands-On!',
            googleFormsLink: "https://forms.gle/LcWfHB1sqehzpt9i8"
		},
        {
			title: 'CodeForge',
			date: '3rd April, 9AM - 5PM',
			description: 'The VarAInce Hackathon',
            googleFormsLink: ""
		},
        {
			title: 'AI Film-Making',
			date: '3rd April, 1:30PM - 4:30PM',
			description: 'Craft Your Cinematic Vision with AI - From Story to Screen!',
            googleFormsLink: "https://forms.gle/HhtHZdKuPMufmWHF8",
		},
        {
			title: 'ML Arena',
			date: '4th April, 9AM - 1PM',
			description: 'Step Into the World of Machine Learning',
            googleFormsLink: "https://forms.gle/aKoURtCXeVas78fA9",
		},
        {
			title: 'Invest(AI)Q',
			date: '4th April, 9AM - 1:30PM',
			description: 'Decode, Invest, Tranform',
            googleFormsLink: "https://forms.gle/pehxLq7CJq6cgYPVA",
		},
        {
			title: 'Bid Wars',
			date: '4th April, 9AM - 1PM',
			description: 'Bid it to Win it!',
            googleFormsLink: "https://forms.gle/i74adSRfSE2feL67A",
		},
	];
</script>

<div bind:this={element} class="{visible ? 'timeline-visible' : 'timeline-hidden'} max-w-screen">
    <p class="font-bold text-center text-6xl text-white">Timeline of Events</p>
    <p class="font-semibold text-center text-3xl text-white m-4">Click on the event to register!</p>
    <div class="relative mx-auto w-full md:w-full">
        {#each events as event, index}
        <div class="flex w-full {index % 2 === 0 ? 'justify-start' : 'justify-end'} relative">
            <div class="absolute top-0 bottom-0 left-1/2 transform -translate-x-1/2 bg-gray-100 w-2 z-0"></div>
            
            <div class="relative w-1/2 p-4">
                <div class="absolute top-5 {index % 2 != 0 ? '-left-3' : '-right-3'} h-6 w-6 rounded-full bg-primary-600 border-4 border-white z-10"></div>
                <button class="p-6 bg-gray-800 rounded-lg shadow-lg cursor-pointer" on:click={() => openModal(event)}>
                    <h3 class="text-white font-bold md:text-2xl text-lg">{event.title}</h3>
                    <p class="text-white text-lg">{event.date}</p>
                    <p class="text-gray-300 text-sm">{event.description}</p>
                </button>
            </div>
        </div>
        {/each}
    </div>
</div>


<Modal bind:open={showModal} size="md" outsideclose>
    <div class="p-6 bg-slate-70 flex flex-col justify-center items-center bg-white">
      {#if selectedEvent}
        <h3 class="text-xl font-bold text-gray-900 dark:text-white">{selectedEvent.title}</h3>
        <p class="mt-2 text-gray-700 dark:text-gray-300">{selectedEvent.description}</p>
        <p class="mt-2 text-sm text-gray-500 dark:text-gray-400">{selectedEvent.date}</p>
        {#if selectedEvent.googleFormsLink !== ""}
        <Button color="green" class="mt-4 w-full"> 
            <a href={selectedEvent.googleFormsLink} target="_blank">Register Here</a>
        </Button>
        {:else}
        <Button color="red" class="mt-4 full disabled">
            Registrations Closed!
        </Button>
        {/if}
      {/if}

    </div>
  </Modal>

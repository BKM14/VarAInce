<script lang="ts">
	import Timeline from '../components/Timeline.svelte';
    import Footer from '../components/Footer.svelte';
	import Headline from '../components/Headline.svelte';
	import NavBar from '../components/NavBar.svelte';
	import Gallery from '../components/Gallery.svelte';
	import { slide } from 'svelte/transition';
	import { onMount } from 'svelte';
	import { backIn } from 'svelte/easing';
    
    let visible = false;
    let element: HTMLElement | null = null;
    let galleryVisible = false;
    let galleryElement: HTMLElement | null = null;

    onMount(() => {
        const observer = new IntersectionObserver(
            ([entry]) => (visible = entry.isIntersecting),
            {threshold: 0.50}
        )
        const galleryObserver = new IntersectionObserver(
            ([entry]) => {
                if (entry.isIntersecting) {
                    setTimeout(() => {
                        galleryVisible = true;
                    }, 200);
                }
            },
            { threshold: 0.30 }
        );
        if (galleryElement) galleryObserver.observe(galleryElement);
        if (element) observer.observe(element);

        return () => {
            observer.disconnect();
            galleryObserver.disconnect();
        };
    });

</script>

<div class="min-h-screen flex flex-col justify-center items-center">

    <NavBar />
    <div class="flex min-h-screen items-center justify-center text-7xl text-white font-extrabold p-10">
        Main SVG
    </div>
	<div bind:this={element} class="max-w-screen relative flex items-center justify-center  p-10 overflow-hidden" id="section1">
        {#if visible}
        <div transition:slide={{duration: 500, easing: backIn}} class="-rotate-25 absolute top-0 right-0 -mr-35  w-1/4">
            <img src="/Rookie.png" alt="Avatar">
        </div>
        {/if}
        <Headline />
    </div>
    <div id="section2" class="flex justify-center items-center ">
        <Timeline/>
    </div>
    <div class="text-7xl text-white font-bold mt-14">Meet the Team</div>
    <div id="section3" class="w-8/10 flex" bind:this={galleryElement}>
        <Gallery eventPhotos={false} galleryTitle="Senior Core Team" leftTile/>
        <Gallery eventPhotos={false} galleryTitle="Junior Core Team"/>
    </div>
    <div class="w-full">
        <Footer />
    </div>
</div>

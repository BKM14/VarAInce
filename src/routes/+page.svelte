<script lang="ts">
	import Timeline from '../components/Timeline.svelte';
    import Footer from '../components/Footer.svelte';
	import Headline from '../components/Headline.svelte';
	import NavBar from '../components/NavBar.svelte';
	import Gallery from '../components/Gallery.svelte';
	import { onMount } from 'svelte';
	import Sponsors from '../components/Sponsors.svelte';
	import { PUBLIC_CLOUDINARY_URL } from '$env/static/public';
    
    let visible = false;
    let element: HTMLElement | null = null;
    let galleryVisible = false;
    let galleryElement: HTMLElement | null = null;

    function handleScroll() {
        if (element) {
            const rect = element.getBoundingClientRect();
            visible = rect.top < window.innerHeight * 0.65 && rect.bottom > 0;
        }
        if (galleryElement) {
            const rect = galleryElement.getBoundingClientRect();
            galleryVisible = rect.top < window.innerHeight * 0.85 && rect.bottom > 0;
        }
    }


    onMount(() => {
        setTimeout(() => {
            handleScroll();

            window.addEventListener('scroll', handleScroll);
        return () => window.removeEventListener('scroll', handleScroll);
        }, 500)
    });

</script>

<div class="md:min-h-screen flex flex-col justify-center items-center w-full">
    <div class="flex flex-col items-center justify-center">
        <NavBar />
        <img src={PUBLIC_CLOUDINARY_URL + "/image/upload/VARAINCEWEEK_o0gptp.png"} alt="" class="box bounce-1 ">
    </div>
    
	<div bind:this={element} class="max-w-screen relative flex items-center justify-center overflow-hidden p-10" id="section1">
        <div 
            class="-rotate-25 absolute top-0 right-0 -mr-35 w-1/4 hidden lg:block"
            class:image-hidden={!visible}
            class:image-visible={visible}
        >
            <img src={PUBLIC_CLOUDINARY_URL + "/image/upload/Rookie_yzheui.png"} alt="Avatar">
        </div>
        <Headline />
    </div>
    <Sponsors />
    <div id="section2" class="flex justify-center items-center my-20">
        <Timeline/>
    </div>
    <div class="text-7xl text-white font-bold mt-14 text-center">The Team</div>
    <div 
        id="section3" 
        class="w-full flex max-w-screen overflow-hidden flex-col md:flex-row"
        bind:this={galleryElement}
        class:image-hidden={!galleryVisible}
        class:image-visible={galleryVisible}
    >
        <Gallery galleryTitle="Senior Core Team" />
        <Gallery galleryTitle="Junior Core Team" />
    </div>
    <div class="w-full">
        <Footer />
    </div>
</div>

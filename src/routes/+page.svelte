<script lang="ts">
	import Timeline from '../components/Timeline.svelte';
    import Footer from '../components/Footer.svelte';
	import Headline from '../components/Headline.svelte';
	import NavBar from '../components/NavBar.svelte';
	import Gallery from '../components/Gallery.svelte';
</script>

<div class="min-h-screen flex flex-col justify-center items-center">

    <NavBar />
    <div class="flex min-h-screen items-center justify-center text-7xl text-white font-extrabold p-10">
        Main SVG
    </div>
	<div class="flex items-center justify-center p-10" id="section1">
        <Headline />
    </div>
    <div id="section2" class="flex justify-center items-center p-40 ">
        <Timeline/>
    </div>
    <div id="section3" class="w-8/10 flex">
        <Gallery eventPhotos={false} galleryTitle="Senior Core Team" leftTile/>
        <Gallery eventPhotos={false} galleryTitle="Junior Core Team"/>
    </div>
    <div class="w-full">
        <Footer />
    </div>
</div>

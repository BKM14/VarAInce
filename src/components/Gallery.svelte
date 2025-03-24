<script lang="ts">
    import { Avatar, Gallery } from "flowbite-svelte";

    const images1 = [
    { alt: 'erbology', src: 'https://flowbite.s3.amazonaws.com/docs/gallery/masonry/image.jpg' },
    { alt: 'shoes', src: 'https://flowbite.s3.amazonaws.com/docs/gallery/masonry/image-1.jpg' },
    { alt: 'small bag', src: 'https://flowbite.s3.amazonaws.com/docs/gallery/masonry/image-2.jpg' }
  ];
  const images2 = [
    { alt: 'plants', src: 'https://flowbite.s3.amazonaws.com/docs/gallery/masonry/image-3.jpg' },
    { alt: 'watch', src: 'https://flowbite.s3.amazonaws.com/docs/gallery/masonry/image-4.jpg' },
    { alt: 'shoe', src: 'https://flowbite.s3.amazonaws.com/docs/gallery/masonry/image-5.jpg' }
  ];
  const images3 = [
    { alt: 'cream', src: 'https://flowbite.s3.amazonaws.com/docs/gallery/masonry/image-6.jpg' },
    { alt: 'small bag', src: 'https://flowbite.s3.amazonaws.com/docs/gallery/masonry/image-7.jpg' },
    { alt: 'lamp', src: 'https://flowbite.s3.amazonaws.com/docs/gallery/masonry/image-8.jpg' }
  ];
  const images4 = [
    { alt: 'toiletbag', src: 'https://flowbite.s3.amazonaws.com/docs/gallery/masonry/image-9.jpg' },
    { alt: 'playstation', src: 'https://flowbite.s3.amazonaws.com/docs/gallery/masonry/image-10.jpg' },
    { alt: 'bag', src: 'https://flowbite.s3.amazonaws.com/docs/gallery/masonry/image-11.jpg' }
  ];

  export let eventPhotos: Boolean = false;
  export let galleryTitle: String = "";
  export let leftTile: Boolean = false;
</script>

<div class="w-3/5 mx-auto p-10">
    <h2 class="text-white font-bold text-6xl text-center m-10">{galleryTitle}</h2>
    {#if eventPhotos}
    <Gallery class="gap-4 grid-cols-2 md:grid-cols-4" items={[]}>
        <Gallery items={images1} />
        <Gallery items={images2} />
        <Gallery items={images3} />
        <Gallery items={images4} />
      </Gallery>
      {:else}
      <Gallery class={`gap-4 grid-cols-2 md:grid-cols-4 ${leftTile ? "border-r-4" : ""}`} items={[]}>
        <Gallery items={images1} let:item>
            <Avatar src={item.src} alt={item.alt} class="w-48 h-38"/>
            <div class="text-white font-bold text-center">Name</div>
            <div class="text-white font-light text-center">Post</div>
        </Gallery>
        <Gallery items={images2} let:item>
            <Avatar src={item.src} alt={item.alt} class="w-48 h-38"/>
            <div class="text-white font-bold text-center">Name</div>
            <div class="text-white font-light text-center">Post</div>
        </Gallery>
        <Gallery items={images3} let:item>
            <Avatar src={item.src} alt={item.alt} class="w-48 h-38"/>
            <div class="text-white font-bold text-center">Name</div>
            <div class="text-white font-light text-center">Post</div>
        </Gallery>
        <Gallery items={images4} let:item>
            <Avatar src={item.src} alt={item.alt} class="w-48 h-38"/>
            <div class="text-white font-bold text-center">Name</div>
            <div class="text-white font-light text-center">Post</div>
        </Gallery>
      </Gallery>
    {/if}
</div>
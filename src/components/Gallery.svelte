<script lang="ts">
    import CustomAvatar from "./CustomAvatar.svelte";
    import type { Profile } from "./CustomAvatar.svelte";
    
    const profiles: Profile[] = [
    { image: 'https://flowbite.s3.amazonaws.com/docs/gallery/masonry/image.jpg', imageAlt: 'erbology', name: 'Alex Carter', post: 'Software Lead' },
    { image: 'https://flowbite.s3.amazonaws.com/docs/gallery/masonry/image-1.jpg', imageAlt: 'shoes', name: 'Jordan Smith', post: 'Hardware Specialist' },
    { image: 'https://flowbite.s3.amazonaws.com/docs/gallery/masonry/image-2.jpg', imageAlt: 'small bag', name: 'Samantha Lee', post: 'Design Head' },
    { image: 'https://flowbite.s3.amazonaws.com/docs/gallery/masonry/image-3.jpg', imageAlt: 'plants', name: 'Rahul Mehta', post: 'AI Engineer' },
    { image: 'https://flowbite.s3.amazonaws.com/docs/gallery/masonry/image-4.jpg', imageAlt: 'watch', name: 'Elena Garcia', post: 'Embedded Systems Expert' },
    { image: 'https://flowbite.s3.amazonaws.com/docs/gallery/masonry/image-5.jpg', imageAlt: 'shoe', name: 'Daniel Brown', post: 'Cybersecurity Analyst' },
    { image: 'https://flowbite.s3.amazonaws.com/docs/gallery/masonry/image-6.jpg', imageAlt: 'cream', name: 'Priya Sharma', post: 'Machine Learning Lead' },
    { image: 'https://flowbite.s3.amazonaws.com/docs/gallery/masonry/image-7.jpg', imageAlt: 'small bag', name: 'Lucas Johnson', post: 'Full Stack Developer' },
    { image: 'https://flowbite.s3.amazonaws.com/docs/gallery/masonry/image-8.jpg', imageAlt: 'lamp', name: 'Sophia Williams', post: 'Robotics Engineer' },
    { image: 'https://flowbite.s3.amazonaws.com/docs/gallery/masonry/image-9.jpg', imageAlt: 'toiletbag', name: 'Ethan Martinez', post: 'Game Developer' },
    { image: 'https://flowbite.s3.amazonaws.com/docs/gallery/masonry/image-10.jpg', imageAlt: 'playstation', name: 'Olivia Kim', post: 'Cloud Architect' },
    { image: 'https://flowbite.s3.amazonaws.com/docs/gallery/masonry/image-11.jpg', imageAlt: 'bag', name: 'Michael Anderson', post: 'Blockchain Specialist' }
  ];

  export let galleryTitle: String = "";
</script>

<div class="w-full md:w-3/5 mx-auto p-10">
  <div>
    <h2 class="text-white text-xl font-bold md:text-3xl text-center md:m-10 mb-4">{galleryTitle}</h2>
    <div class="grid grid-cols-3 lg:grid-cols-4 gap-4">
      {#each profiles as profile}
      <CustomAvatar profile={profile}/>
      {/each}
    </div>
  </div>
</div>
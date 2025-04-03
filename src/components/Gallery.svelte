<script lang="ts">
    import CustomAvatar from "./CustomAvatar.svelte";
    import type { Profile } from "./CustomAvatar.svelte";

    export let galleryTitle: String = "";

    const seniorProfiles: Profile[] = [
    { image: '/senior-core/Arvindhan_Shekhar.jpeg', imageAlt: 'Arvindhan Shekhar', name: 'Arvindhan Shekhar'},
    { image: '/senior-core/Raghav_Katyal.jpeg', imageAlt: 'Raghav Katyal', name: 'Raghav Katyal'},
    { image: '/senior-core/Ibadur_Rahman.jpeg', imageAlt: 'Ibadur Rahman', name: 'Ibadur Rahman'},
    { image: '/senior-core/Krish_Agarwal.jpeg', imageAlt: 'Krish Agarwal', name: 'Krish Agarwal'},
    { image: '/senior-core/Insiya_Vakhariya.jpeg', imageAlt: 'Insiya Vakharia', name: 'Insiya Vakharia'},
    { image: '/senior-core/Kumar_Aditya.jpeg', imageAlt: 'Kumar Aditya', name: 'Kumar Aditya'},
    { image: '/senior-core/Prajwal_JB.jpeg', imageAlt: 'Prajwal JB', name: 'Prajwal JB'},
    { image: '/senior-core/Khavya_Reddy.jpeg', imageAlt: 'Khavya Reddy', name: 'Khavya Reddy'},
    { image: '/junior-core/Yeshved_Salelkar.jpeg', imageAlt: 'Yeshved Salelkar', name: 'Yeshved Salelkar'}
  ];

  const juniorProfiles: Profile[] = [
    { image: '/junior-core/Rishit_Udikeri.jpeg', imageAlt: 'Rishit Udikeri', name: 'Rishit Udikeri'},
    { image: '/junior-core/Angeline_Lewis.jpeg', imageAlt: 'Angeline Lewis', name: 'Angeline Lewis'},
    { image: '/junior-core/Devika_B.jpeg', imageAlt: 'Devika B', name: 'Devika B'},
    { image: '/junior-core/Diya_Rajesh.jpeg', imageAlt: 'Diya Rajesh', name: 'Diya Rajesh'},
    { image: '/junior-core/Rakshitha_C.jpeg', imageAlt: 'Rakshitha C', name: 'Rakshitha C'},
    { image: '/junior-core/Rohit_Harish.jpeg', imageAlt: 'Rohit Harish', name: 'Rohit Harish'},
    { image: '/junior-core/Sai_Prashanth.jpeg', imageAlt: 'Sai Prashanth', name: 'Sai Prashanth'},
    { image: '/junior-core/Sharanya_Sandur.jpeg', imageAlt: 'Sharanya Sandur', name: 'Sharanya Sandur'},
    { image: '/junior-core/Tanisha_Shinthray.jpeg', imageAlt: 'Tanisha Shinthray', name: 'Tanisha Shinthray'},
  ]

  
</script>

<div class="w-full md:w-3/5 mx-auto p-10">
  <div>
    <h2 class="text-white text-xl font-bold md:text-3xl text-center md:m-10 mb-4">{galleryTitle}</h2>
    <div class="grid grid-cols-3 gap-4">
      {#if galleryTitle === "Senior Core Team"}
      {#each seniorProfiles as profile}
      <CustomAvatar profile={profile}/>
      {/each}
      {:else}
      {#each juniorProfiles as profile}
      <CustomAvatar profile={profile}/>
      {/each}
      {/if}
    </div>
  </div>
</div>
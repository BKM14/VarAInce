<script lang="ts">
	import { PUBLIC_CLOUDINARY_URL } from "$env/static/public";
    import CustomAvatar from "./CustomAvatar.svelte";
    import type { Profile } from "./CustomAvatar.svelte";

    export let galleryTitle: String = "";

    const seniorProfiles: Profile[] = [
    { image: PUBLIC_CLOUDINARY_URL + "/image/upload/Arvindhan_Shekhar_klqi1d.jpg", imageAlt: 'Arvindhan Shekhar', name: 'Arvindhan Shekhar'},
    { image: PUBLIC_CLOUDINARY_URL + "/image/upload/Raghav_Katyal_lyhfo5.jpg", imageAlt: 'Raghav Katyal', name: 'Raghav Katyal'},
    { image: PUBLIC_CLOUDINARY_URL + "/image/upload/Ibadur_Rahman_swyn4p.jpg", imageAlt: 'Ibadur Rahman', name: 'Ibadur Rahman'},
    { image: PUBLIC_CLOUDINARY_URL + "/image/upload/Krish_Agarwal_uwbu7c.jpg", imageAlt: 'Krish Agarwal', name: 'Krish Agarwal'},
    { image: PUBLIC_CLOUDINARY_URL + "/image/upload/Insiya_Vakhariya_s6jr4g.jpg", imageAlt: 'Insiya Vakharia', name: 'Insiya Vakharia'},
    { image: PUBLIC_CLOUDINARY_URL + "/image/upload/Kanishka_Sharma_oyolma.jpg", imageAlt: 'Kanishka Sharma', name: 'Kanishka Sharma'},
    { image: PUBLIC_CLOUDINARY_URL + "/image/upload/Kumar_Aditya_zomxk9.jpg", imageAlt: 'Kumar Aditya', name: 'Kumar Aditya'},
    { image: PUBLIC_CLOUDINARY_URL + "/image/upload/Prajwal_JB_htvkfs.jpg", imageAlt: 'Prajwal JB', name: 'Prajwal JB'},
    { image: PUBLIC_CLOUDINARY_URL + "/image/upload/Khavya_Reddy_dy98am.jpg", imageAlt: 'Khavya Reddy', name: 'Khavya Reddy'},
    { image: PUBLIC_CLOUDINARY_URL + "/image/upload/Yeshved_Salelkar_lozsrw.png", imageAlt: 'Yeshved Salelkar', name: 'Yeshved Salelkar'}
  ];

  const juniorProfiles: Profile[] = [
    { image: PUBLIC_CLOUDINARY_URL + "/image/upload/Rishit_Udikeri_zusmv8.jpg", imageAlt: 'Rishit Udikeri', name: 'Rishit Udikeri'},
    { image: PUBLIC_CLOUDINARY_URL + "/image/upload/Angeline_Lewis_yggmcc.jpg", imageAlt: 'Angeline Lewis', name: 'Angeline Lewis'},
    { image: PUBLIC_CLOUDINARY_URL + "/image/upload/Devika_B_pnmtxe.jpg", imageAlt: 'Devika B', name: 'Devika B'},
    { image: PUBLIC_CLOUDINARY_URL + "/image/upload/Diya_Rajesh_gavk1t.jpg", imageAlt: 'Diya Rajesh', name: 'Diya Rajesh'},
    { image: PUBLIC_CLOUDINARY_URL + "/image/upload/Rakshitha_C_rvkdiu.jpg", imageAlt: 'Rakshitha C', name: 'Rakshitha C'},
    { image: PUBLIC_CLOUDINARY_URL + "/image/upload/Rohit_Harish_yjbg1o.jpg", imageAlt: 'Rohit Harish', name: 'Rohit Harish'},
    { image: PUBLIC_CLOUDINARY_URL + "/image/upload/Sai_Prashanth_p31inh.jpg", imageAlt: 'Sai Prashanth', name: 'Sai Prashanth'},
    { image: PUBLIC_CLOUDINARY_URL + "/image/upload/Sharanya_Sandur_b6adtg.jpg", imageAlt: 'Sharanya Sandur', name: 'Sharanya Sandur'},
    { image: PUBLIC_CLOUDINARY_URL + "/image/upload/Tanisha_Shinthray_w2mzkx.jpg", imageAlt: 'Tanisha Shinthray', name: 'Tanisha Shinthray'},
  ]

  
</script>

<div class="w-full md:w-3/5 mx-auto p-10">
  <div>
    <h2 class="text-white text-xl font-bold md:text-3xl text-center md:m-10 mb-4">{galleryTitle}</h2>
    <div class="grid grid-cols-3 gap-4">
      {#if galleryTitle === "Senior Core Team"}
      {#each seniorProfiles as profile, index}
      <div class={index == seniorProfiles.length - 1 ? "col-start-2" : ""}>
        <CustomAvatar profile={profile}/>
      </div>
      {/each}
      {:else}
      {#each juniorProfiles as profile}
      <CustomAvatar profile={profile}/>
      {/each}
      {/if}
    </div>
  </div>
</div>
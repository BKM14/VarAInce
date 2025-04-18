<script lang="ts">
	import { PUBLIC_CLOUDINARY_URL } from "$env/static/public";
</script>

<div class="flex justify-center items-center flex-col">
    <h3 class="text-5xl text-white font-bold">Powered By</h3>
    <div class="flex flex-col lg:flex-row w-4/5 justify-center items-center">
        <div class="w-2/3 h-2/3 lg:w-1/3 lg:h-1/3 m-4">
            <img src={PUBLIC_CLOUDINARY_URL + "/image/upload/sponsor1_peunpy.jpg"} alt="Sponsor1">
        </div>
        <div class="w-2/3 h-2/3 lg:w-1/3 lg:h-1/3 m-4">
            <img src={PUBLIC_CLOUDINARY_URL + "/image/upload/sponsor2_tqcexr.jpg"} alt="Sponsor1">
        </div>
        <div class="w-2/3 h-2/3 lg:w-1/3 lg:h-1/3 m-4">
            <img src={PUBLIC_CLOUDINARY_URL + "/image/upload/sponsor3_rcpf4k.jpg"} alt="Sponsor1">
        </div>
    </div>
</div>

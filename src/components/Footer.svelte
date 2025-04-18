<script>
	import { PUBLIC_CLOUDINARY_URL } from "$env/static/public";
</script>
<footer class="relative py-2 w-full z-50 bg-slate-900/80 flex justify-between">
    <div class="my-auto">
        <a href="/" >
            <img alt="" width="63" height="63" src={PUBLIC_CLOUDINARY_URL + "/image/upload/varaince_ai_o8uatp.png"} style="color: transparent;">
        </a>
    </div>
    <div class="flex items-center text-center">
        <h2 class="text-white font-bold text-xl md:text-2xl lg:text-4xl">VarAInce BMSCE</h2>
    </div>
    <div class="flex my-auto">
        <a href="https://www.linkedin.com/company/varaince-club/" class="text-gray-400 mx-2 hover:text-white"><img alt="LinkedIn" width="32" height="32" src={PUBLIC_CLOUDINARY_URL + "/image/upload/linkedin_c7i8sm.png"} style="color: transparent;"></a>
        <a href="https://www.instagram.com/varaince_bmsce/" class="text-gray-400 mx-2 hover:text-white"><img alt="Instagram" width="32" height="32" src={PUBLIC_CLOUDINARY_URL + "/image/upload/instagram_hx6fia.png"} style="color: transparent;"></a>
    </div>
</footer>
<script lang="ts">
	import { PUBLIC_CLOUDINARY_URL } from '$env/static/public';
	import '../app.css';
	let { children } = $props();
</script>

<div
	class="bg-fixed bg-cover bg-no-repeat"
	style={`background-image: url('${PUBLIC_CLOUDINARY_URL}/image/upload/bg_en0dkq.png')`}
>
	{@render children()}
</div>

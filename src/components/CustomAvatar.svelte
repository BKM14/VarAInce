<script context="module" lang="ts">
	export interface Profile {
		image: string;
		imageAlt: string;
		name: string;
	}
</script>

<script lang="ts">
	import { Avatar } from 'flowbite-svelte';
	import { onMount } from 'svelte';
	export let profile: Profile;

	let visible = false;
	let el: HTMLElement;

	const lazyLoad = (target: Element) => {
		const io = new IntersectionObserver((entries, observer) => {
			entries.forEach((entry) => {
				if (entry.isIntersecting) {
					visible = true;
					observer.disconnect();
				}
			});
		});

		io.observe(el);
	};

	onMount(() => {
		lazyLoad(el);
	});
</script>

<div class="text-center" bind:this={el}>
	<Avatar
		src={visible ? profile.image : undefined}
		alt={profile.imageAlt}
		class="mx-auto h-22 w-23 lg:h-36 lg:w-38"
	/>
	<div class="font-bold text-white">{profile.name}</div>
</div>

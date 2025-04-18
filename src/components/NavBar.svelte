<script>
	import { PUBLIC_CLOUDINARY_URL } from '$env/static/public';
	import { Navbar, NavBrand, NavLi, NavUl, NavHamburger } from 'flowbite-svelte';
	const links = [
		{ href: '#section1', label: 'About Us!' },
		{ href: '#section2', label: 'Timeline' },
		{ href: '#section3', label: 'Meet the Team' }
	];
</script>

<Navbar class="bg-transparent">
	<NavBrand href="/">
		<img src={PUBLIC_CLOUDINARY_URL + "/image/upload/varaince_ai_o8uatp.png"} class="me-3 h-6 sm:h-9" alt="Flowbite Logo" />
		<span class="self-center text-4xl font-semibold whitespace-nowrap text-white">VarAInce</span>
	</NavBrand>
	<NavHamburger />
	<NavUl
		ulClass="flex flex-col mt-4 md:flex-row md:space-x-8 md:mt-0 hover:text-slate-900 md:text-sm md:font-medium bg-transparent border-0"
	>
		{#each links as link (link.href)}
			<NavLi href={link.href} class="text-lg font-bold text-end text-white ">{link.label}</NavLi>
		{/each}
	</NavUl>
</Navbar>

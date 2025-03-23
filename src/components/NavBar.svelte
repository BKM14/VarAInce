<script>
	import { Navbar, NavBrand, NavLi, NavUl, NavHamburger } from 'flowbite-svelte';
	import { onMount } from 'svelte';
	const links = [
		{ href: '/', label: 'Download the App!' },
		{ href: '/about', label: 'Timeline!' },
		{ href: '/docs/components/navbar', label: 'Headline' },
		{ href: '/pricing', label: 'FAQ' }
	];
</script>

<Navbar class="bg-transparent">
	<NavBrand href="/">
		<img src="favicon.png" class="me-3 h-6 sm:h-9" alt="Flowbite Logo" />
		<span class="self-center text-4xl font-semibold whitespace-nowrap text-white">VarAInce</span>
	</NavBrand>
	<NavHamburger />
	<NavUl
		ulClass="flex flex-col mt-4 md:flex-row md:space-x-8 md:mt-0 hover:text-slate-900 md:text-sm md:font-medium bg-transparent border-0"
	>
		{#each links as link (link.href)}
			<NavLi href={link.href} class="text-lg font-bold text-white">{link.label}</NavLi>
		{/each}
	</NavUl>
</Navbar>

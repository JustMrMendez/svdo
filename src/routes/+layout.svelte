<script>
	import BaseNav from '$lib/components/base-nav.svelte';
	import '../app.pcss';

	let links = [
		{ label: 'Home', href: '/' },
		{ label: 'About', href: '/about' },
		{ label: 'Blog', href: '/blog' },
		{ label: 'Contact', href: '/contact' }
	];

</script>

<BaseNav {links} />
<slot />

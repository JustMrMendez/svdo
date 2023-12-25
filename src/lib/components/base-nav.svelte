<script lang="ts">
    type Link = {
        label: string;
        href: string;
    };
    type Props = {
        links?: Link[];
        logo?: string;
    };
	let {
		links = [
			{ label: 'Home', href: '/' },
			{ label: 'About', href: '/about' },
			{ label: 'Blog', href: '/blog' },
			{ label: 'Contact', href: '/contact' }
		],
        logo = 'SVDO'
    } = $props<Props>();
</script>

<nav class="flex justify-between p-2">
	<span class="badge bg-primary-500">{logo}</span>
	<ul class="list-nav flex">
		{#each links as { label, href }}
			<li>
				<a {href}>
					<span class="flex-auto">{label}</span>
				</a>
			</li>
		{/each}
	</ul>
</nav>

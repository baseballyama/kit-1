<script>
	import { Icon } from '@sveltejs/site-kit';
	import '@sveltejs/site-kit/code.css';
	import '$lib/docs/client/docs.css';
	import '$lib/docs/client/shiki.css';
	import * as hovers from '$lib/docs/client/hovers.js';

	/** @type {import('./$types').PageData} */
	export let data;

	hovers.setup();
</script>

<svelte:head>
	<title>{data.section.title} • Docs • SvelteKit</title>

	<meta name="twitter:title" content="SvelteKit docs" />
	<meta name="twitter:description" content="{data.section.title} • SvelteKit documentation" />
	<meta name="Description" content="{data.section.title} • SvelteKit documentation" />
</svelte:head>

<div class="content listify">
	<h1>{data.section.title}</h1>

	<a
		class="edit"
		href="https://github.com/svelte-jp/kit/edit/master/documentation/{data.section.file}"
	>
		<Icon size={50} name="edit" /> Edit this page on GitHub
	</a>

	<section>
		{@html data.section.content}
	</section>

	<div class="controls">
		<div>
			<span class:faded={!data.prev}>previous</span>
			{#if data.prev}
				<a href="/docs/{data.prev.slug}">{data.prev.title}</a>
			{/if}
		</div>

		<div>
			<span class:faded={!data.next}>next</span>
			{#if data.next}
				<a href="/docs/{data.next.slug}">{data.next.title}</a>
			{/if}
		</div>
	</div>
</div>

<style>
	.edit {
		position: relative;
		font-size: 1.4rem;
		line-height: 1;
		z-index: 2;
	}

	.edit :global(.icon) {
		position: relative;
		top: -0.1rem;
		left: 0.3rem;
		width: 1.4rem;
		height: 1.4rem;
		margin-right: 0.5rem;
	}

	.controls {
		max-width: calc(var(--linemax) + 1rem);
		border-top: 1px solid #eee;
		padding: 1rem 0 0 0;
		display: grid;
		grid-template-columns: 1fr 1fr;
		margin: 6rem 0 0 0;
	}

	.controls > :first-child {
		text-align: left;
	}

	.controls > :last-child {
		text-align: right;
	}

	.controls span {
		display: block;
		font-size: 1.2rem;
		text-transform: uppercase;
		font-weight: 600;
		color: var(--second);
	}

	.controls span.faded {
		opacity: 0.4;
	}
</style>

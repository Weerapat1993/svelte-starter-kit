<script context="module">
	export const prerender = true;
</script>

<script lang="ts">
	/**
	 * Home HTML
	 * =====================
	 *
	 * @contributors: Patryk Rzucidło [@ptkdev] <support@ptkdev.io> (https://ptk.dev)
	 *
	 * @license: MIT License
	 *
	 */
	const imports = {
		a: () => import("$lib/components/test-component/a.svelte"),
		b: () => import("$lib/components/test-component/b.svelte"),
		c: () => import("$lib/components/test-component/c.svelte"),
	};

	let component = "a";
</script>

<div id="container">
	<section class="hero is-medium is-primary is-bold">
		<div class="hero-body">
			<div class="container">
				<h1 class="title">About</h1>
				<h2 class="subtitle">svelte-kit-ssr-boilerplate</h2>
			</div>
		</div>
	</section>
	<div class="content has-text-centered">app/pages/about.svelte</div>
	<label>
		<input type="radio" bind:group={component} value="a" />
		a
	</label>

	<label>
		<input type="radio" bind:group={component} value="b" />
		b
	</label>

	<label>
		<input type="radio" bind:group={component} value="c" />
		c
	</label>
</div>

{#await imports[component]() then module}
	<svelte:component this={module.default} />
{/await}

<style>
	h1, figure, p {
		text-align: center;
		margin: 0 auto;
	}

	h1 {
		font-size: 2.8em;
		text-transform: uppercase;
		font-weight: 700;
		margin: 0 0 0.5em 0;
	}

	figure {
		margin: 0 0 1em 0;
	}

	img {
		width: 100%;
		max-width: 400px;
		margin: 0 0 1em 0;
	}

	p {
		margin: 1em auto;
	}

	@media (min-width: 480px) {
		h1 {
			font-size: 4em;
		}
	}
</style>

<!-- <svelte:head>
	<title>Sapper project template</title>
</svelte:head> -->

<!-- <h1>Great success!</h1> -->

<!-- <figure>
	<img alt='Success Kid' src='successkid.jpg'>
	<figcaption>Have fun with Sapper!</figcaption>
</figure> -->

<p><strong>Try editing this file (src/routes/index.svelte) to test live reloading.</strong></p>

<!--  -->

<!-- src/routes/[localeIndex].svelte -->
<script context="module">
	// the (optional) preload function takes a
	// `{ path, params, query }` object and turns it into
	// the data we need to render the page
	export async function preload(page, session) {
		// the `slug` parameter is available because this file
		// is called [slug].svelte
		const { localeIndex } = page.params;

		// `this.fetch` is a wrapper around `fetch` that allows
		// you to make credentialled requests on both
		// server and client
		const res = await this.fetch(`/${localeIndex}`);
		const article = await res.json();

		return { index };
	}
</script>

<script>
	export let index;
</script>

<svelte:head>
	<title>{index.title}<!-- Great success! --></title>
</svelte:head>

<h1>{index.title}</h1>

<figure>
	<img alt='Success Kid' src='successkid.jpg'>
	<figcaption>index.caption<!-- Have fun with Sapper! --></figcaption>
</figure>

<div class='content'>
	{@html index.html}
</div>
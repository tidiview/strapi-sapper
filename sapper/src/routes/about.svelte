<svelte:head>
	<title>About</title>
</svelte:head>

<script>
 
	let myHeaders = new Headers();
	myHeaders.append('Content-Type', 'text/json');
	let myInit = { 
		method: 'GET',
		headers: myHeaders,
		mode: 'cors',
		cache: 'default'
	};
	let request = new Request('http://localhost:1337/restaurants', myInit)
	let promise = getJson();

	async function getJson() {
		const res = await fetch(request);
		const json = await res.json();

		if (res.status === 200) {
			return json[0].description;
			console.log(json[0].description)
		} else {
			throw new Error(json);
			console.log(json)
		}
	}

	/* function handleClick() {
		promise = getJson();
	} */
</script>

<h1>About this site</h1>

<p>This is the 'about' page. There's not much here.</p>

<!-- <button on:click={handleClick}>
	get json
</button> -->

{#await promise}
	<p>...waiting</p>
{:then name}
	<p>The name is {name}</p>
{:catch error}
	<p style="color: red">{error.message}</p>
{/await}
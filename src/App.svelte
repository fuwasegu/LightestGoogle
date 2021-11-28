<script>
let keywords = '';
let apiKey = '';
let id = '';

async　function getSnippet() {
	if (! apiKey) {
		return
	}
	if (! id) {
		return
	}
	if (! keywords) {
		return
	}
	const keyword = keywords.split(/ |　/).join('+');
	const params = {
		'key': apiKey,
		'cx': id,
		'lr': 'lang_ja',
		'q': keyword
	};
	const query_params = new URLSearchParams(params);

	return await fetch('https://customsearch.googleapis.com/customsearch/v1?' + query_params)
		.then(response => response.json())
		.then(response => {
			let results = [];
			response.items.forEach(element => {
				results.push(element.snippet);
			});
			return results;
		});
}

let snippets = getSnippet();

function onClick() {
	snippets = getSnippet();
}

</script>

<main>
	<h1>Welcome to LightestGoogle !</h1>

	<label for="api-key">
		API Key
		<input type="text" name="api-key" id="api-key" bind:value="{apiKey}">
	</label>
	{#if ! apiKey}
	<p style="color: red;">Set Google Cloud Platform API Key.</p>
	{/if}

	<label for="id">
		Search Engine ID
		<input type="text" name="id" id="id" bind:value="{id}">
	</label>
	{#if ! id}
	<p style="color: red;">Set Search Engine ID.</p>
	{/if}

	<input type="text" name="keyword" id="keyword" bind:value="{keywords}">
	<button on:click="{onClick}">検索</button>
	{#if ! keywords}
	<p style="color: red;">Set Search Keywords.</p>
	{/if}

	<hr>
	<h2>検索結果</h2>
	{#await snippets}
		<p>...waiting</p>
	{:then texts}
		<ul>
			{#each texts as text}
				<li>
					{text}
				</li>
			{/each}
	</ul>
	{/await}

</main>

<style>

</style>

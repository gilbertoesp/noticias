<script>
    export let id;

    const fetchNew = (async () => {
        const response = await fetch(`https://hacker-news.firebaseio.com/v0/item/${id}.json?print=pretty`);
        return await response.json();
    })()

</script>

{#await fetchNew}
    <p>Esperando noticias..</p>
{:then data} 
    <article>
        <h3><a target="_blank" rel="noreferrer" href={data?.url}>{data.title}</a></h3>
        <p>Publicado por {data.by}	</p>
    </article>
{/await}

<style>
	article {
		position: relative;
		padding: 0 0 0 2em;
		border-bottom: 1px solid #eee;
	}

	h3 {
		font-size: 2.5rem;
		margin: 0.5em 0;
	}

	a {
		color: blue;
	}
</style>
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
        <h3>{data.title}</h3>  
    </article>
{/await}
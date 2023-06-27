<script>
  import Counter from './lib/Counter.svelte'
  import Form from './lib/Form.svelte'
  
  const PAGE_SIZE = 20;

  const latest_stories = (async () => {
    const res = await fetch(`https://hacker-news.firebaseio.com/v0/newstories.json?print=pretty`)
    return await res.json();
  })()
</script>

<main>

  <div class="list__container">
    <div class="list__header">
      <h1>Noticias para mí</h1>
    </div>
    {#await latest_stories}
      <p>Cargando...</p>
    {:then data} 
      <div class=" list__content">
        {#each data as id}
          <Form {id}></Form>
        {/each}

      </div>
    {/await}
  </div>
</main>

<style>
  h1{
    font-size: 5rem;
    text-align: left;
  }
</style>

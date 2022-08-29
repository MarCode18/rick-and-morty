<script>
  let characters = [];
  let page = 1;

  async function negrito(){
    const response = await fetch('https://rickandmortyapi.com/api/character?page=' + page);
    const data = await response.json();
    console.log(data);
    characters = data.results;
  }

  negrito()

  function nextPage(){
    page++;
    negrito()
  }

  function previousPage(){
    page--;
    negrito()
  }
</script>

<h1 class="titulo">Rick and Morty Svelte</h1>
<div>
  <button class="btn1" on:click={previousPage} disabled={page === 1}>Previous</button>
  <button class="btn2" on:click={nextPage}>Next</button>
</div>
<br>
<div>
  {#each characters as personaje}
  <div>
    <img src="{personaje.image}" alt="{personaje.name}">
    <h1>{personaje.name}</h1>
    <h3>{personaje.species}</h3>
  </div>

  {/each}
</div>
<div>
  <button class="btn1" on:click={previousPage} disabled={page === 1}>Previous</button>
  <button class="btn2" on:click={nextPage}>Next</button>
</div>
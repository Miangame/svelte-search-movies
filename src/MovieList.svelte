<script>
  import Movie from "./Movie.svelte";

  export let responseMovies;

  console.log(responseMovies);
</script>

{#await responseMovies}
  <strong>Loading...</strong>
{:then movies}
  {#each movies as { Title, Year, Poster }}
    <Movie {Title} {Year} {Poster} />
  {:else}
    <strong>No hay resultados</strong>
  {/each}
{:catch error}
  <p>❌ There has been an error</p>
{/await}

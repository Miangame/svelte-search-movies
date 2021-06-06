<script>
  export let Title, Poster, Year;

  const now = new Date();
  const currentYear = now.getFullYear();
</script>

<article>
  <img src={Poster} alt={Title} />
  <h3>{Title}</h3>
  <span>{Year}</span>

  {#if currentYear - Year < 5}
    <i>🆕</i>
  {/if}
</article>

<style>
  article {
    border: 1px solid #eee;
    border-radius: 4px;
    padding: 16px;
    margin-bottom: 8px;
  }

  h3 {
    font-size: 24px;
    margin-bottom: 4px;
  }
</style>

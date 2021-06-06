<script>
  import MovieList from "./MovieList.svelte";

  let value = "";

  let responseMovies = [];

  const handleInput = (event) => {
    value = event.target.value;
  };

  $: if (value.length > 2) {
    responseMovies = fetch(
      `https://www.omdbapi.com/?s=${value}&apikey=422350ff`
    )
      .then((res) =>
        res.ok
          ? res
          : new Error("Something bad happened with the fetching of movies")
      )
      .then((res) => res.json())
      .then((apiResponse) => apiResponse.Search || []);
  }
</script>

<input
  placeholder="Search movies..."
  type="text"
  on:input={handleInput}
  {value}
/>

<MovieList {responseMovies} />

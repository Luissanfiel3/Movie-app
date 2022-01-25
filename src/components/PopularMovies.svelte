<script>
    export let popular;
    console.log(popular[0]);
    import MovieCard from "./MovieCard.svelte";
</script>

<h3>Popular Movies</h3>

<div class="popular-movies">
    {#each popular as movie}
        <MovieCard {movie}/>
    {/each}
</div>


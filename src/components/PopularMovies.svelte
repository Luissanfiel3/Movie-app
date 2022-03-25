<script>
    export let popular;
    import MovieCard from "./MovieCard.svelte";
</script>

    <div class="max-w-2xl mx-auto py-2 px-4 sm:py-4 sm:px-6 lg:max-w-7xl lg:px-8">
        <div class="grid grid-cols-1 gap-y-10 sm:grid-cols-2 gap-x-6 lg:grid-cols-3 xl:grid-cols-5 xl:gap-x-8">
            {#each popular as movie}
                <MovieCard {movie}/>
            {/each}
        </div>
    </div>




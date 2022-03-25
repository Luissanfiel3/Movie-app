<script>
    export let movie;
</script>

<div  class="group">
    <div class="w-full aspect-w-1 aspect-h-1 bg-gray-200 rounded-lg overflow-hidden xl:aspect-w-7 xl:aspect-h-8">
        <a sveltekit:prefetch sveltekit:noscroll href={'/movie/'+movie.id}> <img src="{'https://image.tmdb.org/t/p/w500' + movie.poster_path}"
                                           alt="{movie.title}"
                                           class="w-full h-full object-center object-cover group-hover:opacity-75"></a>
    </div>
    <h3 class="mt-4 text-sm text-gray-700">{movie.title}</h3>
    <p class="mt-1 text-lg font-medium text-gray-900">{movie.release_date}</p>

</div>


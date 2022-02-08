<script>
    export let movie;
</script>

<!--
<div class="movie-card">
    <img src="{'https://image.tmdb.org/t/p/w500' + movie.poster_path}" alt="{movie.title}">
    <div class="description">
        <h2>{movie.title}</h2>
        <p>{movie.release_date}</p>
    </div>
</div>
-->

    <div href="#" class="group">
        <div class="w-full aspect-w-1 aspect-h-1 bg-gray-200 rounded-lg overflow-hidden xl:aspect-w-7 xl:aspect-h-8">
            <a href={'/movie/'+movie.id}>  <img src="{'https://image.tmdb.org/t/p/w500' + movie.poster_path}" alt="{movie.title}"  class="w-full h-full object-center object-cover group-hover:opacity-75"></a>
        </div>
        <h3 class="mt-4 text-sm text-gray-700">{movie.title}</h3>
        <p class="mt-1 text-lg font-medium text-gray-900">{movie.release_date}</p>

    </div>

<style>
   /* img {
        width: 100%;
        height: 45vh;
       !* object-fit:cover;
        border-radius:0.5rem;
        margin-bottom: 1rem;*!
    }*/

   /* h2 {
        font-size: 0.9rem;
    }*/

   /* .description {
      height: 5vh;
    }*/

   /* p {
        font-size:0.7rem;
    }*/

   /* .movie-card {
        display:flex;
        flex-direction:column ;
        justify-content: space-around;
        padding: 1rem;
    }*/

</style>

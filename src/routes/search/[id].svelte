<script context="module">

    export async function load({fetch, params}) {
        const res = await fetch(
            `https://api.themoviedb.org/3/search/movie?api_key=dbc077badfb6e17e163999796d1a1f66&language=en-US&query=${params.id}&page=1&include_adult=false`
        );

        const data = await res.json();
        if (res.ok) {
            return {
                props: {searchedMovie: await data.results}
            }
        }
    }


</script>

<script>
    import MovieCard from "../../components/MovieCard.svelte";
    import NavComponent from "../../components/NavComponent.svelte";
    import HomeTitle from "../../components/HomeTitle.svelte";
    import SeachMovies from "../../components/SeachMovies.svelte";
    import {fly} from 'svelte/transition'
    import Footer from "../../components/Footer.svelte";

    export let searchedMovie;
</script>
<NavComponent/>
<div >
    <HomeTitle/>
    <SeachMovies/>
    <div class="bg-gray-100" in:fly={{y:50, duration:400}} out:fly={{y:50, duration:400}}>
        <div class="grid grid-cols-1 gap-y-10 sm:grid-cols-2 gap-x-6 lg:grid-cols-3 xl:grid-cols-5 xl:gap-x-8">
            {#each searchedMovie as movie}
                <MovieCard {movie}/>
            {/each}
        </div>
    </div>
</div>
<Footer/>

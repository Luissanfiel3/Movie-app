<script context="module">
    export async function load({fetch}) {
        const res = await fetch(
            `https://api.themoviedb.org/3/movie/popular?api_key=dbc077badfb6e17e163999796d1a1f66&language=en-US&page=1`
        );

        const data = await res.json();
        if (res.ok) {
            return {
                props: {popular: data.results}
            }
        }
    }
</script>

<script>

    import PopularMovies from '../components/PopularMovies.svelte';
    import NavComponent from "../components/NavComponent.svelte";
    import Footer from "../components/Footer.svelte";
    import SeachMovies from "../components/SeachMovies.svelte";
    import HomeTitle from "../components/HomeTitle.svelte";

    export let popular;
</script>

<NavComponent/>
<!-- image search box -->


<div class="bg-gray-100">
    <HomeTitle/>
    <SeachMovies/>
    <PopularMovies {popular}/>
    <Footer/>
</div>
<style>

</style>



<script context="module">

    export async function load({fetch, params}) {

        const res = await fetch(
            `https://api.themoviedb.org/3/movie/${params.id}?api_key=dbc077badfb6e17e163999796d1a1f66&language=en-US`
        );

        const resVideo = await fetch(
            `https://api.themoviedb.org/3/movie/${params.id}/videos?api_key=dbc077badfb6e17e163999796d1a1f66`
        );

        let movieDetail = await res.json();
        let releaseDate;

        const videoDetail = await resVideo.json();
        let videoKey;

        let movieId = 0;
        if (res.ok && resVideo.ok) {

            let convertDate = new Date(movieDetail.release_date);
            releaseDate = convertDate.toLocaleDateString('en-GB',
                {day: '2-digit', month: 'short', year: 'numeric'})

            videoKey = videoDetail.results[0].key
            movieId = movieDetail.id

            return {
                props: {movieDetail, movieId, videoKey, releaseDate}
            }
        }
            return {
            props: movieDetail = null,
            };


    }


</script>

<script>
    import NavComponent from "../../components/NavComponent.svelte";
    import Footer from "../../components/Footer.svelte"
    import ErrorPage from "../../components/ErrorPage.svelte"
    import {fly} from 'svelte/transition'

    export let movieDetail, videoKey, releaseDate, movieId;

</script>

<NavComponent/>
<div class="container mx-auto m-0 " in:fly={{y:50, duration:400}} out:fly={{y:10, duration:500,delay:10}}>

    <section class="bg-white dark:bg-gray-800 my-0">
        {#if movieId }
            <div class="container flex flex-col m-0 px-6  mx-auto space-y-6 lg:h-[32rem] lg:py-16 lg:flex-row lg:items-center">
                <div class="flex items-center justify-center w-full h-96 lg:w-1/2">
                    <!--                <img class="object-cover w-full h-full mx-auto rounded-md lg:max-w-2xl"-->
                    <!--                     src={'https://image.tmdb.org/t/p/original' + movieDetail.backdrop_path} alt={movieDetail.title}/>-->
                    <iframe class="rounded-lg shadow-2xl" width="560" height="315"
                            src="https://www.youtube.com/embed/{videoKey}"
                            title="YouTube video player" frameborder="0"
                            allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
                            allowfullscreen></iframe>
                </div>
                <div class="max-w-xl m-0 px-6  lg:max-w-5xl lg:w-1/2">
                    <h2 class="text-2xl font-bold text-gray-800 dark:text-white md:text-3xl">{movieDetail.title} </h2>
                    <p class="mt-4 text-gray-600 dark:text-gray-400">{movieDetail.overview}</p>
                    <p class="mt-4 text-gray-600 dark:text-gray-400">{releaseDate}</p>

                    <div class="mt-8">
                        <!--                    <button class="px-5 py-2 font-semibold text-gray-100 transition-colors duration-200 transform bg-gray-900 rounded-md hover:bg-gray-700" on:click={() => handleToggleModal()}>Abrir modal</button>-->
                        <!--                    <a href="/video" on:click|preventDefault={() => handleToggleModal()}-->
                        <!--                       class="px-5 py-2 font-semibold text-gray-100 transition-colors duration-200 transform bg-gray-900 rounded-md hover:bg-gray-700">Start-->
                        <!--                        Now</a>-->
                    </div>
                </div>
            </div>
        {:else}
            <h1>error</h1>
            <!--            <ErrorPage/>-->
        {/if}
    </section>
</div>
<Footer/>




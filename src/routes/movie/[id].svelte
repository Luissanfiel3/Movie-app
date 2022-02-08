<script context="module">
    export async function load({fetch, params}) {
        console.log(params.id)
        const res = await fetch(
            `https://api.themoviedb.org/3/movie/${params.id}?api_key=dbc077badfb6e17e163999796d1a1f66&language=en-US`
        );

        const movieDetail = await res.json();
        console.log(movieDetail);
        if (res.ok) {

            return {
                props: {movieDetail}
            }
        }
    }
</script>

<script>
    import NavComponent from "../../components/NavComponent.svelte";

    export let movieDetail;
</script>

<NavComponent/>
<div class="container mx-auto">
    <section class="bg-white dark:bg-gray-800 py-5">


        <div class="container flex flex-col px-6 py-10 mx-auto space-y-6 lg:h-[32rem] lg:py-16 lg:flex-row lg:items-center">
            <div class="flex items-center justify-center w-full h-96 lg:w-1/2">
                <img class="object-cover w-full h-full mx-auto rounded-md lg:max-w-2xl"
                     src={'https://image.tmdb.org/t/p/original' + movieDetail.backdrop_path} alt={movieDetail.title}/>
            </div>
            <div class="max-w-xl px-6 py-12 lg:max-w-5xl lg:w-1/2">
                <h2 class="text-2xl font-bold text-gray-800 dark:text-white md:text-3xl">{movieDetail.title} </h2>
                <p class="mt-4 text-gray-600 dark:text-gray-400">{movieDetail.overview}</p>
                <p class="mt-4 text-gray-600 dark:text-gray-400">{movieDetail.release_date}</p>

                <div class="mt-8">
                    <a href="#"
                       class="px-5 py-2 font-semibold text-gray-100 transition-colors duration-200 transform bg-gray-900 rounded-md hover:bg-gray-700">Start
                        Now</a>
                </div>
            </div>


        </div>
    </section>
</div>

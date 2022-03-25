<script>
    let inputValue = '';
    let active = false;
    import {goto} from "$app/navigation";

    function submitSearch() {
        if (inputValue){

            goto('/search/'+ inputValue.toLocaleLowerCase());
        }

    }

</script>

<div class="max-w-2xl mx-auto py-2 px-4 sm:py-4 sm:px-6 lg:max-w-7xl lg:px-8">

    <div class="bg-white items-center justify-between w-full flex rounded-full shadow-lg p-2 mb-5 sticky"
         style="top: 5px">
        <div>

            <div class="p-2 mr-1 rounded-full hover:bg-gray-100 cursor-pointer">
                <svg class="h-6 w-6 text-gray-500" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20"
                     fill="currentColor">
                    <path fill-rule="evenodd"
                          d="M9.707 16.707a1 1 0 01-1.414 0l-6-6a1 1 0 010-1.414l6-6a1 1 0 011.414 1.414L5.414 9H17a1 1 0 110 2H5.414l4.293 4.293a1 1 0 010 1.414z"
                          clip-rule="evenodd"/>
                </svg>
            </div>
        </div>

        <input on:focus={() => (active = true)} bind:value={inputValue}
               class="font-bold uppercase rounded-full w-full py-4 pl-4 text-gray-700 bg-gray-100 leading-tight focus:outline-none focus:shadow-outline lg:text-sm text-md"
               type="text" placeholder="Search">


        <button on:click|preventDefault={submitSearch} >
            <div class="bg-gray-500 p-2 hover:bg-blue-400 cursor-pointer mx-2 rounded-full">
                <svg  class="w-6 h-6 text-white"
                     xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" >
                    fill="currentColor">
                    <path fill-rule="evenodd"
                          d="M8 4a4 4 0 100 8 4 4 0 000-8zM2 8a6 6 0 1110.89 3.476l4.817 4.817a1 1 0 01-1.414 1.414l-4.816-4.816A6 6 0 012 8z"
                          clip-rule="evenodd"/>
                </svg>
            </div>
        </button>
    </div>
</div>

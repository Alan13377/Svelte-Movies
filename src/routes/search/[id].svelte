<script context="module">
import { dataset_dev } from "svelte/internal";
    export async function load({fetch,params}){ 
        const response = await fetch(`https://api.themoviedb.org/3/search/movie?api_key=6f6a8ae60bfbc11f439583921b9326c1&language=es-US&query=${params.id}&page=1&include_adult=false`);
        const data = await response.json()
        if(response.ok){
            return{
                props:{searchMovie:data.results}
            }
        }
    } 
</script>

<script>
    import MovieCard from "../../components/MovieCard.svelte";
    export let searchMovie;
</script>

<div class="search-movies">
    {#each searchMovie as movie}
         <MovieCard {movie}></MovieCard>
    {/each}
</div>

<style>
    .search-movies{
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
        grid-row-gap:2rem;
        gap: 2rem;
    }
</style>
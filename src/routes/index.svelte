<script context="module">
     export async function load({fetch}){ 
        const response = await fetch(`https://api.themoviedb.org/3/movie/popular?api_key=6f6a8ae60bfbc11f439583921b9326c1&language=es-US&page=1`)
        const data = await response.json()
        console.log(data)
        if(response.ok){
            return{
                props:{popular:data.results}
            }
        }
    } 

  
</script>

<script>
    import PopularMovies from "../components/PopularMovies.svelte";
    import SeachMovies from "../components/SeachMovies.svelte";
    export let popular
</script>

<section>

    <SeachMovies></SeachMovies>
    <PopularMovies popular={popular} />

</section>

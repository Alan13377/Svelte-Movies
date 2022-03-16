<script>
    let inputValue = ""
    let active = false
    import {goto} from "$app/navigation"
    function cancelInactive(){
        if(inputValue){
            active = true
        }else{
            active = false
        }
    }
    function submitSearch(){
        goto("/search/"+inputValue)
    }
</script>
<form on:submit|preventDefault={submitSearch} class="search">
    {#if !active }
        
    <label for="search">Search</label>
    {/if}
    <input on:blur={cancelInactive} on:focus={() => active = true} bind:value={inputValue} type="text" id="search">
    <button>Search</button>
</form>

<style>
    button {
        background-color: #4CAF50;
        color: white;
        padding: 14px 20px;
        margin: 8px 0;
        border: none;
        cursor: pointer;
        
    }
    input{
        width: 100%;
        padding: 12px 20px;
        margin: 8px 0;
        display: inline-block;
        border: 1px solid #ccc;
        border-radius: 4px;
        box-sizing: border-box;
    }
</style>
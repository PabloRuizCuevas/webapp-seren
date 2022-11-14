
<script lang="ts">
    import { fade } from 'svelte/transition';
    export let promise: any = null

    interface Files {
        accepted: any,
        rejected: any
    }

    export let files: Files

    async function handleClick(){
        promise = true
        if (files.accepted.length === 0){
            console.log('nothing here')
        }
        console.log('aqui')
        
        my_promise = Promise.all(files.accepted.map(async file => {
            await uploadFile(file);
        }));
        
    }

    let my_promise : Promise<any> | null  = null

async function uploadFile(file: any){
    const formData = new FormData();
    formData.append('name', file.name);
    formData.append('dataFile', file);
    const upload = fetch('http://localhost:8080/file', {
        method: 'POST',
        body: formData,
        mode: 'cors'
    })
    
    return upload
}
      
</script>

<button on:click={handleClick}> Submmit Files </button>

{#if promise != null }
    {#await my_promise}
        <p transition:fade>...waiting</p>
    {:then response}
        <p>The number: is {response}</p>
    {:catch error}
        <p style="color: red">{error.message}</p>
    {/await}
{/if}

<style>
    

</style>

<script lang="ts">
    import { fade } from 'svelte/transition';
    import Download from "./Download.svelte"
    export let loadList: Boolean = false;

    let root_ip: string = 'http://127.0.0.1:8000';
    let my_promise: Promise<any> | null  = null
    //let status: Promise<any> | null  = null

    interface Files {
        accepted: any,
        rejected: any
    }

    export let files: Files

    async function sendFiles(){
        
        if (files.accepted.length === 0){
            console.log('nothing here')
            return
        }
        loadList = true
        console.log('aqui')
        
        my_promise = Promise.all(files.accepted.map(async (file: any) => {
            await uploadFile(file);
        })); 
    }


    async function uploadFile(file: any){
        const formData = new FormData();
        formData.append('name', 'file.name');
        formData.append('file', file);
        const upload = fetch(`${root_ip}/upload-file`, {
            method: 'POST',
            body: formData,
            mode: 'no-cors'
        })
        return upload
    }

    async function test(file: any){
        const upload = fetch(`${root_ip}/test`, {
            method: 'GET'
        })
        console.log('request ')
        return upload
    }
      
</script>

<button on:click={sendFiles}> Submmit Files </button>

{#if loadList != false}
    {#await my_promise}
        <p> Sending files ... </p>
    {:then}
        <p transition:fade style="color: green;">Files uploaded !</p>
        <Download></Download>
    {:catch error}
        <p style="color: red">{error.message}</p>
    {/await}
{/if}


<style>
 p{
    text-align: center;
 }
</style>